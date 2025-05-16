# Dynamic KNN-CNN with Graph Neural Networks for Image Classification

This project introduces a new approach to image classification by combining convolutional neural networks (CNNs) with dynamically constructed K-nearest neighbor (KNN) graphs. The idea is to enhance traditional feature extraction by learning meaningful relationships between image regions, and then modeling those relationships with graph neural networks (GNNs).

The broader motivation behind this project is to create a flexible framework that can convert any type of data into a graph structure. Once we have that structure, we can apply powerful graph-based learning techniques for tasks like classification, segmentation, and more.

## Project Overview

In conventional image classification, CNNs are effective at capturing spatial patterns. However, they often miss out on structural relationships between different regions in an image. This project aims to address that by treating the image as a graph, where nodes represent high-level features and edges represent learned relationships between them.

Instead of using a fixed KNN graph, this model learns the optimal number of neighbors (`k`) during training. As a result, each image in the dataset constructs its own personalized graph structure, leading to more adaptive and context-aware feature representation.

We start with the EMNIST Letters dataset for experimentation, but the method is general and can be applied to other types of images.

## Methodology

The model consists of several components:
- An **Encoder Block** that applies convolution and pooling operations to extract feature maps.
- A **KNN Block** that transforms these feature maps into graph nodes and predicts the best `k` value for each image.
- A **GNN Block** that constructs the graph using the predicted `k` and applies SAGEConv layers for learning.
- A **Pooling and Classification Block** that aggregates the learned features and outputs a prediction.

During training, we observe that the model learns to adjust the distribution of `k` over time. Early in training, the model favors higher `k` values, but gradually shifts to smaller, more focused graphs, which likely capture more meaningful relationships.

## Dataset

The initial experiments were conducted on the EMNIST Letters dataset:
- 124,800 training images
- 20,800 test images
- Each image is a 28x28 grayscale representation of a handwritten letter

The dataset was split into training and validation sets during model development.

## Results

The model shows strong performance on the EMNIST test set, achieving an accuracy of 94.31%, which is competitive with several recent benchmarks.
Training and validation curves are stable, and the learned `k` values evolve in a way that suggests the model is effectively learning how to structure its graphs.


## Get in Touch

This work is still in progress. If you're interested in collaborating, trying the method on new datasets, or improving the model further, feel free to reach out.

Contact:  
Farid Taghiyev  
farid1taghiyev@gmail.com
