# Image Classification and Object Localization

This project aims to create a Convolutional Neural Network (CNN) for image classification and object localization tasks. Specifically, it focuses on classifying the main subject in an image and localizing it by drawing bounding boxes around the object.

## Overview

The project utilizes the [MNIST dataset](http://yann.lecun.com/exdb/mnist/) to synthesize a custom dataset for the task. Each "digit" image is placed on a black canvas with dimensions 75 x 75 at random locations. Additionally, the corresponding bounding boxes for these "digits" are calculated.

The bounding box prediction is modeled as a regression task, meaning that the model predicts numeric values representing the coordinates of the bounding box (xmin, ymin, xmax, ymax).

## Dataset Preprocessing

To prepare the data for training and validation, the project defines several helper functions:

- `read_image_tfds`: This function overlays the "digit" image on top of a larger canvas with random placement.
- `get_training_dataset`: Loads and splits the data to create the training set.
- `get_validation_dataset`: Loads and splits the data to create the validation set.

## CNN Architecture

The custom CNN architecture consists of the following components:

- `feature_extractor`: Convolutional layers responsible for feature extraction from the input image.
- `classifier`: The output layer that predicts among 10 categories (digits 0 through 9).
- `bounding_box_regression`: The output layer that predicts 4 numeric values defining the coordinates of the bounding box (xmin, ymin, xmax, ymax).
- `final_model`: A combination of the feature extraction, classification, and bounding box prediction layers. This architecture is an example of a branching model, as it produces two types of outputs (category and numeric values).

## Model Training

To train the model:

- Select the optimizer and metrics appropriate for the task.
- Compile the model.
- Train the model for a specific number of epochs, depending on desired performance and available time. Each epoch should take only a few seconds if a TPU is utilized.

## Model Evaluation

The project evaluates the model's performance using Intersection over Union (I-O-U) metric to measure the accuracy of bounding box predictions.

## Visualizing Predictions

The code in the project visualizes predictions, showing both the classification and the predicted bounding boxes. True bounding box labels are displayed in green, while model-predicted bounding boxes are shown in red. The predicted digit is also displayed beneath the image.



