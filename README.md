# Fashion Image Generation using GANs

## Project Overview

This project implements a **Generative Adversarial Network (GAN)** to generate fashion images from a custom dataset sourced from Polyvore. The Dataset can be accessed [here](https://github.com/AemikaChow/AiDLab-fAshIon-Data/blob/main/Datasets/cleaned-maryland.md). The primary goal is to explore how GANs can create realistic images that may assist in fashion recommendations.

## Authors
- **Sajjad Saed**
- **Kamand Kalashi**

## Steps Involved

### 1. Dataset Preparation
- The dataset consists of fashion images organized by class labels.
- Each image is resized to **128x128 pixels** and converted to grayscale.
- Images are normalized and split into training and test sets to ensure effective training and evaluation.

### 2. GAN Architecture

#### Generator
- **Input**: Noise vector of dimension 100.
- **Layers**:
  - Dense layer reshaping the input into a feature map of size (8, 8, 512).
  - Multiple **Conv2DTranspose** layers to upsample the image to (128, 128).
  - Final layer with **tanh activation** to produce the generated image.

#### Discriminator
- **Input**: Images of size (128, 128, 1).
- **Layers**:
  - Several **Conv2D** layers for downsampling.
  - A Flattening layer followed by a Dense layer with **sigmoid activation** to classify images as real or fake.

### 3. Model Compilation
- The **Discriminator** is compiled with:
  - Optimizer: **Adam** (with learning rate decay).
  - Loss function: **Binary cross-entropy**.
- The **GAN model** integrates the Generator and Discriminator, freezing the Discriminator during Generator training.

### 4. Model Training
- The model is trained over **150 epochs** with a **batch size of 32**.
- Training alternates between training the Discriminator and Generator, with learning rates adjusted as training progresses.

### 5. Results Visualization
- Loss and accuracy plots for both Generator and Discriminator are created for each epoch.
- Sample images generated by the Generator are visualized to evaluate the quality.

## Requirements
Install the following libraries to run the project:

- `NumPy`
- `OpenCV`
- `TensorFlow`
- `Keras`
- `Matplotlib`
- `Seaborn`

## Conclusions
This project demonstrates how GANs can generate fashion images that closely resemble real images from the dataset. The results highlight GANs' potential in the fashion industry, particularly for virtual try-ons and fashion recommendations. Future enhancements may focus on improving image quality with more advanced GAN architectures or integrating the GAN with recommendation engines to enhance user experience in fashion selection.
