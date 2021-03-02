# malaria-diagnose-project
MSDS692 Spring2021 Project


# 'Using Machine Learning to Diagnose Malaria'


# Indtroduction

According to the CDC, malaria is, "...a serious and sometimes fatal disease caused by a parasite that commonly infects a certain type of mosquito which feeds on humans." Those with malaria generally develop mild to severe fever and flu-like symptoms; in some cases, serious complications occur that can be life-threatening such as blood clots, severe anemia, seizures, and comas. Each year, nearly 290 million people become infected with malaria, and over 400,000 end up dying from the disease (MayoClinic, 2021). 

The process of detecting infection is usually done by trained laboratory professionals using a microscope-- a process that can take over an hour per sample. In underserved areas, this can be a problem because there are often too many patients and not enough resources. By automating the process with machine learning, this can improve accuracy/efficiency,  reduce cost, and help more patients affected by this disease.

The purpose of this project is to explore deep learning techniques and CNNs in order to create a model that accurately predicts malaria infection in blood smear data.

![image](https://user-images.githubusercontent.com/70441161/109417348-83dcea00-7980-11eb-882f-4484f5fc1022.png)

Image 1: Malaria lifecycle and areas of low, medium, and high transmittal.

# Methods & Analysis

# 1. Data Science Methods & Data Aquisition
- Machine Learning --> Deep Learning --> Convolutional Neural Networks --> Classification
- Data: Kaggle 'Malaria Cell Images Dataset: Images for Detecting Malaria.' Retrieved from: https://www.kaggle.com/iarunava/cell-images-for-detecting-malaria
- Dataset contains 2 directories (Parasitized & Uninfected) each containing 13,800 images each. Total images in the dataset equal 27,600.

![image](https://user-images.githubusercontent.com/70441161/109717596-7f245b80-7b63-11eb-863a-40e5bbe7546a.png)

Image 2: Sample of what is contained in the two directories.

# 2. Environment Set-Up
- Linux OS --> Anaconda --> Jupyter Notebook --> Tensorflow --> Python

I first imported all required Tensoflow and Python APIs for the project: 
- Sequential: a model in Tensorflow that allows you to build a model layer by layer. There are pre-built models with a certain number of layers already built in, but I wanted to build my own so that I could maybe understand what is going on better since this is my first time working with deep learning and CNNs.
- ImageDataGenerator: allows for editing images in the dataset in real time.
- Optimizers: help train the model.
- Other APIs: numpy, pandas, matplotlib

# 3. Model Set-up
- Data image augmentation using ImageDataGenerator. This step resizes the image and also sets-up the model to recognize the images in any orientation and distortion.
- Validation_split is used to create an 80/20 split between the data; where 80% of the images are contained in the train_set for model training, and 20% of the images are contained in the validation_set in order to validate the training.

# 4. Building the Model
CNN Components: Convolution --> ReLU --> MaxPooling --> Flattening --> Full Connection --> Compiling

I built my model 4 layers deep. As an example, Layer #1 begins with the convolution layer denounced as Conv2D. Conv2D is typically used for CNNs, and it has mandatory parameters that have to be entered which consists of filters, kernel size, strides and padding. Input shape is the height and width of the image and 3 means it’s a colored image. It also contains MaxPooling and Dropout layer. MaxPooling helps the model learn how to recognize an image in any orientation and distortion, while Dense keeps the model keep the model from overfitting by randomly dropping some of the outputs in the layer. If set to 0.2, it means that Dropout set to 20%, so 1 in 5 will be randomly dropped.

Layer #3 introduces Flatten and Dense. Flatten turns the pooling into a 1-dimensional array. Dense is the fully connected layer, which is where pooling and flattening come together and classification happens. 

Each layer uses the ReLU function to introduce non-linearity to each layer.

Compiling is the last step before actually running the model, it defines what optimizer is being used, how loss/error/or deviations will be found in the model, and then metrics defines how the model will be evaluated. Metrics was set to 'accuracy' because I want to see how accurate my model is for the problem defined.

# References

![image](https://user-images.githubusercontent.com/70441161/109467866-0c16ca00-7a29-11eb-8217-ca8c62dfa49a.png)
![image](https://user-images.githubusercontent.com/70441161/109467319-416ee800-7a28-11eb-9d32-0fc28236b70c.png)

