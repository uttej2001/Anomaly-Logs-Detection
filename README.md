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
We establish User Data for specific time intervals. This time span might range from a few hours to several weeks. Depending on the use case, the profiles could include basic counting vectors like total counts and average unit(day/week/hour) counts, as well as more advanced network calls vectors like upload/download ratio.

We implement kmeans to cluster the points that are furthest from all clusters combined after the feature space is formed, and the points that are farthest from all clusters joined are labeled anomaly. W e apply the sum of squared distances from the centroids. To weigh outliers more strongly than others, we apply squared distance rather than absolute distance (similar to using MAE vs MSE).

While Euclidean distance in feature space is one option, Isolation forest takes a different approach. Isolation forest count the number of splits necessary to reach a specific point; the fewer splits needed, the more 'isolated' and hence anomaly the point is.

## Architecture
![image](https://user-images.githubusercontent.com/72940291/148746550-8cd7a437-bb35-44f8-8d33-27b61a71331f.png)
