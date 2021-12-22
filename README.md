# Unsupervised-Learning
This project is part of CSE 574 - Introduction to Machine Learning

**Project Overview:**

The goal of the project is to perform unsupervised learning on Cifar-10 dataset. In the first part of the project, I have performed K-means clustering on the raw data from scratch. 
Then, I have used Silhouette analysis and Dunn index are used to evaluate the model. In the second part, I have performed k-means clustering on the representations generated by Auto-Encoder.

**Dataset:**

Cifar-10 dataset has a training set of 50,000 examples, and a test set of 10,000 examples.
Each example is a 32x32 image, associated with a label from 10 classes. Each image is 32 
pixels in height and 32 pixels in width, for a total of 1024 pixels in total.
The dataset is divided into 5 training batches and 1 testing batch, each with 10000 images. 
The test batch contains exactly 1000 random selected images from each class and training 
batches contain exactly 5000 images from each class. There is no overlap in the classes.
Below is the representation of some images from Cifar-10 dataset:

![image](https://user-images.githubusercontent.com/42407754/147023558-a5a9d005-2ea7-479b-84ea-59bd2b99ab4a.png)

**Python Editor:**

I have used Jupiter Notebook on Google Collab for implementation and shared.

**Data Pre-Processing:**

We gray scale the images, hence making the size of the initial array (10,000 * (32,32,3)) to 10,000*(32,32)

 **Model Building:**
 
 **Part -1 : Implementing K-Means Clustering:**

**K-Means function:**

1. Select K samples at random from the dataset to be the initial clusters. (Let K be 10).
2. Calculate the Euclidean distance between every object and the centroid.
3. Now assign the objects to the nearest cluster.
4. For each of the k clusters, update the cluster centroids by calculating the mean of 
all the data points in that cluster.
5. Iteratively repeat step 3 & 4 until we reach terminate condition i.e., the error is less 
than tolerance (0.0001) or the iterations reach the assigned max_iterations.

![image](https://user-images.githubusercontent.com/42407754/147023794-5befdbf9-0d82-4401-84fc-240dd787ac71.png)

![image](https://user-images.githubusercontent.com/42407754/147023827-b7f0d7d1-10a7-46eb-b2eb-5cf2f5dcd97c.png)

**Visualizing the final clusters:**

- We assign different colours to 10 clusters and run Principal Component Analysis (PCA) 
which reduces the dimensions of the dataset to 1024.
- Now, we use a scatter plot to visualize the final clusters as below.

![image](https://user-images.githubusercontent.com/42407754/147023887-8d628b84-307c-4da5-a5f8-2d3aefd89ac1.png)

**Part – 2: Implementing Convolutional Auto-Encoder:**

- As a first step, we import tensorflow and necessary libraries from Keras.
- "Autoencoding" is a data compression algorithm where the compression and decompression 
functions are 1) data-specific, 2) lossy, and 3) learned automatically from examples rather 
than engineered by a human. Additionally, in almost all contexts where the term 
"autoencoder" is used, the compression and decompression functions are implemented with 
neural networks.

![image](https://user-images.githubusercontent.com/42407754/147023946-9efa292e-1504-4786-a82a-5e982596bcfe.png)

- After data preprocessing and model training, we get the results as below:

![image](https://user-images.githubusercontent.com/42407754/147024056-ef1591de-8c52-436a-991a-61f11783cf67.png)

**Generating clusters using K-Means from the sparse representations generated by 
the Auto-Encoder:**

- We pass the encoded images generated from Convolutional AutoEncoder to KMeans 
function to generate clusters.
- Using Pairwise_distance function from sklearn, we calculate the distance between every 
pair of samples
- Finally, we print the Silhouette score and Dunn’s index.

![image](https://user-images.githubusercontent.com/42407754/147024116-8ee0ef17-a0b7-4ba9-86ef-67681ae7196a.png)
