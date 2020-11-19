---
template: post
title: Feature Extraction using Image Processing
slug: /feature-extraction
draft: true
date: 2019-11-14T18:29:10.066Z
description: >-
  In this blog, we are going to discuss one of the important pre-steps to any
  CNNs or image based deep learning called feature extraction. We are going to
  learn more about it with Image Processing and OpenCV library.
category: Image Processing
tags:
  - image processing
---
**What is Feature Extraction?**

Feature extraction is a part of the dimensionality reduction process, in which, an initial set of the raw data is divided and reduced to more manageable groups. So when you want to process it will be easier. The most important characteristic of these large data sets is that they have a large number of variables. These variables require a lot of computing resources to process them. So Feature extraction helps to get the best feature from those big data sets by select and combine variables into features, thus, effectively reducing the amount of data. These features are easy to process, but still able to describe the actual data set with the accuracy and originality.

**Why Feature Extraction is Useful?**

The technique of extracting the features is useful when you have a large data set and need to reduce the number of resources without losing any important or relevant information. Feature extraction helps to reduce the amount of redundant data from the data set.

In the end, the reduction of the data helps to build the model with less machine’s efforts and also increase the speed of learning and generalization steps in the machine learning process.

**Applications of Feature Extraction**

**Bag of Words- Bag-of-Words** is the most used technique for natural language processing. In this process they extract the words or the features from a sentence, document, website, etc. and then they classify them into the frequency of use. So in this whole process feature extraction is one of the most important parts.

**Image Processing** –Image processing is one of the best and most interesting domain. In this domain basically you will start playing with your images in order to understand them. So here we use many many techniques which includes feature extraction as well and algorithms to detect features such as shaped, edges, or motion in a digital image or video to process them.

**Auto-encoders**: The main  purpose of the auto-encoders is efficient data coding which is unsupervised in nature. this process comes under unsupervised learning . So Feature extraction procedure is applicable here to identify the key features from the data to code by learning from the coding of the original data set to derive new ones.

**How to Store Images in the Machine?**

So in this section, we will start with from scratch. For the first thing, we need to understand how a machine can read and store images. Loading the image, read them and then process them through the machine is difficult because the machine does not have eyes like us.

Let’s have a look at how a machine understands an image.Machines see any images in the form of a matrix of numbers. The size of this matrix actually depends on the number of pixels of the input image.

What is pixel?

The Pixel Values for each of the pixels stands for or describe how bright that pixel is, and what color it should be. So In the simplest case of the binary images, the pixel value is a 1-bit number indicating either foreground or background.So pixels are the numbers, or the pixel values which  denote the intensity or brightness of the pixel.Smaller numbers which is closer to zero helps to represent black, and the larger numbers which is closer to 255 denote white.So this is the concept of pixels and how machine sees the images without eyes through the numbers. feature extraction in Image processingBut, for the case of a coloured image, we have  three Matrices or the channels

Red,

Green

and Blue.

So in these three matrices, each of the matrix has values between 0-255 which represents the intensity of the colour of that pixel. If you  have a coloured image like the dog image we have in the above image on the left. so being a human you have eyes so you can see and can say it is a dog coloured image. But how computer can understand it is coloured or black and white image? So you can see we also have a three matrices which represents the channel of RGB – (for the three color channels – Red, Green, and Blue) On the right, we have three matrices. These three channels are superimposed and used to form a coloured image.  So this is how a computer can differentiate between the images.

 **Introduction to OpenCV:**

There are some predefined packages and libraries are there to make our life simple. One of the most important and popular libraries is Opencv. It helps us to develop a system which can process images and real-time video using computer vision. OpenCv focused on image processing, real-time video capturing to detect faces and objects.

**Background of OpenCV:**

 OpenCV was invented by  Intel in 1999 by Gary Bradsky. The first release was in the year 2000. OpenCV stands for Open Source Computer Vision Library. This Library is based on optimised C/C++ and it supports Java and Python along with C++ through interfaces. 

OpenCV is one of the most popular and successful libraries for computer vision and it has an immense number of users because of its simplicity, processing time and high demand in computer vision applications. OpenCV-Python is like a python wrapper around the C++ implementation. OpenCv has more than 2500 implemented algorithms which are freely available for commercial purpose as well.

**Applications of OpenCV:**

Medical image analysis: We all know image processing in the medical industry is very popular.  Let’s take an example:

**Identify Brain tumour**: Every single day almost thousands of patients are dealing with brain tumours. There are many software which are using OpenCv to detect the stage of the tumour using an image segmentation technique. One of the applications is RSIP Vision which builds a probability map to localize the tumour and uses deformable models to obtain the tumour boundaries with zero level energy.

**Object Detection**: Detecting objects from the images is one of the most popular applications. Suppose, You want to detect a person sitting on a two-wheeler vehicle without a helmet which is equivalent to a defensible crime. So you can make a system which detects the person without a helmet and captures the vehicle number to add a penalty. There are many applications there using OpenCv which are really helpful and efficient. These applications are also taking us towards a more advanced world with less human efforts.

I'm going to elaborate more on object detection in my further blogs.If you have any requests I should cover please post it in the comments
