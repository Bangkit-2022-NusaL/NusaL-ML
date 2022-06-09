# NusaL-ML
Bangkit 2022 Product-based Capstone Project - NusaL - ML

This is Machine Learning repository for NusaL application.

NusaL Machine Learning model is made with Google Colaboratory to provide Indonesia's local language's font recognition.

## Introduction

This is NusaL - Nusantara Language Machine Learning repository. 

## Deployment Data

### Load Datasets
- The dataset that we use from kaggle (https://www.kaggle.com/datasets/phiard/aksara-jawa) and github (https://github.com/ridhomujizat/AksaraSundaCNN/)

### Training the Data
- Using `tf.keras.losses.CategoricalCrossentropy` as loss
- Using `Adam(learning_rate=5e-4)` as optimizer
- Added more layer too to model.Sequential to make model accuracy more better:
  - Added `Conv2D(256, (5,5), activation = 'relu', padding = 'same', input_shape=(112,112,1))` layer
  - Added `LeakyReLU(alpha=0.2)` layer
  - Added `MaxPooling2D(2,2)` layer
  - Added `Conv2D(256, (5,5))` layer
  - Added `LeakyReLU(alpha=0.3)` layer
  - Added `MaxPooling2D(2,2)` layer
  - Added `Conv2D(128, (5,5))` layer
  - Added `LeakyReLU(alpha=0.3)` layer
  - Added `MaxPooling2D(2,2)` layer
  - Added `Dropout(0.2)` layer
  - Added `GlobalMaxPool2D()` layer
  - Added `Dense(1024)` layer
  - Added `LeakyReLU(alpha=0.2)` layer
  - Added `Dense(18, activation ='softmax')` layer #depends on how many the language has
- Training with 100 epochs
- From the result, got:
  - `loss: 2.82%`
  - `accuracy: 98.89%`
  - `val_loss: 29.98%`
  - `val_accuracy: 91.46%`

## Deployment
- After build the model, we save the model and convert it to tensorflow lite 
- `converter = tf.lite.TFLiteConverter.from_keras_model(model)`
- `tflite_model = converter.convert()`


## Library
Library used for developing NusaL :
- Tensorflow
- matplotlib.pyplot
- numpy
