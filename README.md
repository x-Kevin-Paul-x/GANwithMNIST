# MNIST GAN Image Generation

## Overview

This project implements a Generative Adversarial Network (GAN) using TensorFlow and Keras to generate realistic images of handwritten digits from the MNIST dataset. The project demonstrates the capabilities of GANs in learning the distribution of the MNIST digits and generating new samples that closely resemble the original data.

## Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Model Architecture](#model-architecture)
- [Training the GAN](#training-the-gan)
- [Saving Generated Images](#saving-generated-images)
- [Results](#results)

## Repository Structure

- **`README.md`**: This file, providing an overview and instructions for the project.
- **`MNIST_GAN.ipynb`**: Google Colab script containing the GAN model implementation and training loop.
- **`generated_images/`**: Directory where generated images will be saved during training.

## Getting Started

### Prerequisites

To run this project, you need the following dependencies:

- Python 3.7+
- TensorFlow 2.x
- Numpy
- Matplotlib

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/x-Kevin-Paul-x/GANwithMNIST.git
   cd MNIST-GAN-Image-Generation
   ```

2. **Install the required dependencies:**
   ```bash
   pip install tensorflow numpy matplotlib
   ```

## Model Architecture

The project consists of two main models:

### Generator
The generator takes a random noise vector as input and generates an image that mimics the MNIST digits. The architecture includes:

- Dense layers with LeakyReLU activation and BatchNormalization.
- Final Dense layer reshaped to the desired image shape with `tanh` activation.

### Discriminator
The discriminator is a binary classifier that differentiates between real MNIST images and images generated by the generator. The architecture includes:

- Flattening of the input image.
- Dense layers with LeakyReLU activation.
- Final Dense layer with a `sigmoid` activation function to output a probability.

### GAN Model
The GAN model combines the generator and discriminator. During training, the generator tries to fool the discriminator by producing images that the discriminator classifies as real.

## Training the GAN

The training process involves:

1. **Loading the MNIST dataset**: Preprocessed to normalize the pixel values between -1 and 1.
2. **Training the Discriminator**: On a batch of real and generated images to distinguish between them.
3. **Training the Generator**: By feeding random noise and attempting to fool the discriminator into classifying the generated images as real.

### Running the Training

To start training the GAN:

```bash
python gan_mnist.py
```

By default, the model is trained for 10,000 epochs with a batch size of 128. You can adjust these parameters in the `train_gan` function.

## Saving Generated Images

The `save_imgs` function saves a grid of generated images every 100 epochs (configurable). The images are saved in the `generated_images/` directory with filenames corresponding to the epoch number.

## Results

During training, the model prints out the discriminator's loss and accuracy, as well as the generator's loss at each epoch. The generated images can be found in the `generated_images/` directory, showcasing the progression of the generator's ability to create realistic digits.
