# CryptoClustering

Cryptocurrency Clustering

This project clusters cryptocurrencies based on their price change data using K-Means clustering. Principal Component Analysis (PCA) is also applied to optimize the clustering process by reducing dimensionality.

Project Overview

This project involves:
	1.	Scaling and normalizing cryptocurrency data.
	2.	Finding the optimal number of clusters (k) using the elbow method.
	3.	Clustering cryptocurrencies using K-Means.
	4.	Visualizing clusters in both the original feature space and a reduced feature space via PCA.

Table of Contents

	1.	Data Preparation
	2.	Finding the Optimal k Value
	3.	Clustering Cryptocurrencies
	4.	Optimizing Clusters with PCA
	5.	Visualizing Results
	6.	Conclusion

Data Preparation

	1.	Load the data from the CSV file and use StandardScaler() from scikit-learn to normalize it.
	2.	Create a DataFrame with the scaled data and set the “coin_id” index from the original DataFrame as the index for the new DataFrame.
	3.	Verify the scaled data by displaying the first five rows.

Finding the Optimal k Value

To determine the optimal number of clusters (k), the elbow method is used on both the scaled data and the PCA-transformed data.

Steps:
	1.	Create a list of potential k values (1 to 11).
	2.	For each k, compute the inertia (sum of squared distances) and store it.
	3.	Plot the inertia values to visually identify the optimal k where the curve bends (“elbow”).

This process is repeated for both the scaled and PCA-transformed data, and the optimal k value for each is identified and compared.

Clustering Cryptocurrencies

Clustering with Scaled Data

	1.	Initialize the K-Means model with the best k value.
	2.	Fit the model and predict clusters for each cryptocurrency.
	3.	Add the predicted clusters to a copy of the scaled DataFrame.
	4.	Create a scatter plot using hvPlot:
	•	Set the x-axis as price_change_percentage_24h and the y-axis as price_change_percentage_7d.
	•	Color points by cluster labels.
	•	Use hover_cols to display the “coin_id” for each point.

Clustering with PCA Data

	1.	Repeat the clustering steps above, but using the PCA-transformed data.
	2.	Plot the clusters with hvPlot:
	•	Set the x-axis as PC1 and the y-axis as PC2.
	•	Color points by cluster labels.
	•	Use hover_cols to display “coin_id” for each point.

Optimizing Clusters with PCA

	1.	Perform PCA on the scaled data to reduce it to three principal components.
	2.	Calculate the explained variance for each component and determine the total variance explained by these three components.
	3.	Create a new DataFrame for the PCA-transformed data with “coin_id” as the index.

Visualizing Results

Visualize the clusters in both the original feature space and the PCA-reduced space to compare clustering effectiveness.
	•	Original Space: Plot clusters based on price_change_percentage_24h and price_change_percentage_7d.
	•	PCA Space: Plot clusters using PC1 and PC2.

Conclusion

Using PCA to reduce the feature space can enhance clustering clarity by focusing on primary variance directions and reducing noise, allowing for more efficient and interpretable clustering.
