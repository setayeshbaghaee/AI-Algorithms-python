## Neural Network From Scratch 

This project contains two neural network implementations built entirely from scratch using NumPy, without relying on deep learning frameworks such as TensorFlow or PyTorch.

The main goal of this project was to gain a deeper understanding of the mathematical and computational mechanics behind neural networks. — not just use high-level libraries, but manually implement forward propagation, backpropagation, loss computation, regularization, and optimization.

The repository includes:

Notebook 1: A general-purpose neural network focused on regression and learning fundamentals

Notebook 2: A dataset-specific neural network tuned for MNIST digit classification

## Project Structure

### Ann_project2 (1).ipynb
A step-by-step implementation starting from linear regression and extending to a multi-layer neural network (regression task).

### mnistmodel.ipynb
A fully connected neural network specifically designed and tuned for the MNIST handwritten digit dataset.

## Notebook 1 — General Neural Network (Regression)

This notebook is structured as a learning journey. It builds intuition first, then gradually increases model complexity.

Part 1: Data Preprocessing & Linear Regression Baseline

Manual feature standardization

Train/test split

Linear regression implemented from scratch

Mean Squared Error (MSE) loss

Gradient Descent parameter updates

Basic visualization and performance analysis

The dataset is loaded from housing_data.csv, with median_house_value as the target column.

This baseline helps establish a reference point before moving to a neural network.

Part 2: Multi-Layer Neural Network (Fully Connected)

After building linear regression, the model is extended into a deeper neural network.

Architecture

Input: 8 features

Hidden layers: 16 → 64 → 64 → 16

Output: 1 value (regression)

batch_size=64

learning_rate = 0.1

lambda_reg = 0.01

Implemented Components

Manual weight and bias initialization

ReLU activation function

Forward propagation

Backpropagation (including ReLU derivatives)

MSE loss = 0.0221601913466981

L2 regularization applied to weights

Stochastic Gradient Descent (SGD) training

This notebook focuses on understanding the mechanics of neural networks rather than optimizing performance for a specific dataset.

## Notebook 2 — MNIST Classification Model

This notebook applies the same core ideas to a real-world classification problem: handwritten digit recognition (MNIST).

Unlike Notebook 1, this model is tuned specifically for MNIST.

Data & Preprocessing

The notebook expects:

mnist_train.csv

mnist_test.csv

Dataset format:

First column: label

Remaining 784 columns: pixel values

Preprocessing steps:

Pixel normalization to the range [0, 1]

One-Hot encoding for labels

Data shuffling at each epoch

Architecture

Input layer: 784

Hidden layers: 256 → 128 → 64 → 32

Output layer: 10 classes

Hidden activations: ReLU

Output activation: Softmax

Loss & Training

Cross-Entropy Loss

Mini-batch Gradient Descent

batch_size = 100

epochs = 20

learning_rate = 0.1

lambda_reg = 0.01

Data shuffled every epoch

train accuracy: 100.00%

test accuracy: 98.05%

Final loss: 0.1164


This configuration achieves strong classification performance while remaining a pure NumPy implementation.

## Dependencies

numpy

pandas

scikit-learn

matplotlib

seaborn

tqdm

plotly (optional)

Install them with:

pip install numpy pandas scikit-learn matplotlib seaborn tqdm plotly

## How to Run
```bash

git clone https://github.com/setayeshbaghaee/neural-network-from-scratch.git
cd neural-network-from-scratch
jupyter notebook
```

Then open either notebook and run the cells sequentially.

Important Note About Datasets

The repository does not include dataset files.

To run:

For Notebook 1:

Place housing_data.csv in the same directory.
It must include a median_house_value column.

For Notebook 2:

Place:

mnist_train.csv

mnist_test.csv

in the same directory as the notebook.

## What I Learned

Implementing backpropagation manually makes gradient flow much clearer.

The pairing of Softmax and Cross-Entropy is crucial for stable classification training.

Regularization directly impacts generalization.

Hyperparameter choices (learning rate, batch size, epochs) significantly affect convergence.

Even a pure NumPy implementation can achieve strong performance on MNIST.

## Possible Improvements

Add Adam optimizer

Implement Dropout

Add Early Stopping

Refactor into a reusable class-based module

Extend to Convolutional Neural Networks (CNNs)

## Author

Setayesh Baghaee
