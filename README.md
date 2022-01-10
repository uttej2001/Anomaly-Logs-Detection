# Anomaly-Logs-Detection

There are many studies done to detect anomalies based on logs. Current approaches are mainly divided into three categories: supervised learning methods, unsupervised learning methods, and deep learning methods. Many supervised learning methods are used for log-based anomaly detection.

## Dataset
The dataset is a logs data from a remote server generated for 1 month. This dataset is created, post cleaning and picking only relevant events on which we wish to identify anomalies by Kibana.
This data has three columns:
- timestamp: timestamp describes when the login happens.
- id: The id field gives the unique identity of the users.
- ip_address: These Ip addresses are of user’s Operating System.
- Total data that is used to detect anomalies is 721547 rows x 3 columns (timestamp, user_id and ip_address)
![image](https://user-images.githubusercontent.com/72940291/148744601-9552c8ba-c828-4dbc-b46e-50237477aa3d.png)

## Approach
We create Profiles for User-IP over certain time periods. This time period can vary from few hours to few weeks. The profile can include basic count vectors such as total counts, average unit(day/week/hour) counts to complex network calls vectors such as upload/download ratio based on the use case. 

In this repo we use basic count and frequency vectors. With profiles in hand, we can use ML algorithms to identify anomalies.

## ML Approach
Once the feaure space is generated, we use kmeans to cluster and the points which are farther from all clusters combined are considered anomalous. We use sum of squared distances from the centroids in this repo. We use squared distance instead of absolute distance to weigh the outliers more than others(similar to using MAE vs MSE).

While euclidean distance in the feature space is one way to look at it, Isolation forest offers a unique approach to this problem. Isolation trees see the number of splits it take to reach a certain point, the lesser splits required, the more `isolated` the point is and hence, anomalous.
