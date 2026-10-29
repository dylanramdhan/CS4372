# CS 4372: Assignment #3
## Assignment #3 - Deep Learning with Keras
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

Dataset: [Dog Breed Identification](https://www.kaggle.com/competitions/dog-breed-identification)

### Summary
In this assignment, we are exploring Deep Learning using Keras (Transfer Learning). This project builds an image classifier that identifies a dog’s breed from a photo, using Kaggle’s Dog Breed Identification dataset (10,222 labeled images across 120 breeds, split 70% / 15% / 15% into training, validation, and test sets). Rather than training a model from scratch, it uses transfer learning with a MobileNetV2 base pre-trained on ImageNet, in two stages: feature extraction, where the base is frozen and only a new classification head is trained, and fine-tuning, where the top layers of the base are unfrozen and trained at a much lower learning rate. Six experiments compared data augmentation, learning rate, dropout, and the number of unfrozen layers, with every decision based on validation accuracy. The final model, fine-tuned on its top 30 layers, reached 76.9% test accuracy. Built in Google Colab with TensorFlow/Keras; the dataset is downloaded at runtime through the Kaggle API.


### How To Run The Code
Since we do all the pip installs at the beginning the code should just run as typed. We don't do any external imports outside of what has already been installed at the beginning.
