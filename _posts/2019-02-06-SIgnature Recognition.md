---
published: true
title: Signature Recognition
date: 2019-02-06T00:00:00.000Z
tags: AI predict CNN KNN genuine forged Signature
categories: project
future: true
---
## Signature Recognition
The post is written about an AI model which can predict the forgery and genuineness of a Signature sample. <br>

## Problem Statement
In organizations like banks where the Authenticity of the signature of a person is very important, there still doesn't exist any autonomous system which can predict forgery of a signature.

Artificial Intelligence is the field of computer science that emphasizes on creating intelligent systems and through which
a machine can learn to make decisions, I have been working in this field for a while, so I decided to solve this problem with the help of some knowledge that I have been able to gain in past few years.

## The Idea

In organizations like banks, they basically have the database of every customer hence I made my model accordingly.
So let's dive into the technicalities now.
### Dataset ---
I used various Online datasets available for the model. The idea was to have a number of samples of every person/customer including genuine as well as forged signatures to make a `person dependent system`.
Luckily I found various online datasets of the same manner online. I used Dutch as well as English signatures so as to increase the dataset


### Preprocessing --
<img src="https://i.imgur.com/OUDPlgG.png" alt="drawing" width="200"/><img src="https://i.imgur.com/S6c5Uei.png" alt="drawing" width="200"/>

The **Right** image is the *genuine* signature and the **left** one is the *forged* one.

the first problem was to remove the effects of different inks from the image as it can be of any form.
hence for that, I applied *thinning* to the image by using `morphological functions of sklearn`.

<img src="https://i.imgur.com/uvPZP8T.png" alt="drawing"/>

`here is the image after thinning it`.

The image was also converted to *grayscale* from RGB and was also *normalized* and *smoothed* to negate factors which
could affect the model, every image was also resized to same size i.e **[50,100]**.

<img src="https://i.imgur.com/83rPybZ.png" alt="drawing" width="250"/> <img src="https://i.imgur.com/dgDUceB.png" alt="drawing" width="250"/>

`left is the grayscaled image and right is the smoothed image`

Image Preprocessing is one of the important tasks in deep learning especially in a task like signature
Recognition where small variations can truly affect the model.

### Features Extraction
As this task is not just recognizing dogs or cats or any other classification task, I had to extract
some hand-picked features from the image, here I took help from some research papers I read beforehand.

#### Density of the signature
The Features tells us the ratio of the number of pixels of the signature to the total number of image pixels, for this the image was binarily segmented by open cv after converting it to grayscale.
<img src="https://i.imgur.com/Zf5xkA7.png" alt="drawing" width="200"/>

`here is the binary image through which the ratio was calculated`
#### Compute the number of spatial symbols within the signature Image.


Every person in their signature uses some spatial symbols, such as they use some x marks (cross marks), star marks or
other symbols. The total number of spatial symbols of a person's signature is unique.


<img src="https://i.imgur.com/sLraabm.png" alt="drawing"/> <br>

For calculating the total number of spatial symbols in a signature image we have to preprocess the image up to thinning. Then If we find that one pixel having
more than two neighbors each of which get the values 1 then those pixels will form a Spatial symbol <br>

#### Height/width ratio of the signature
I read in a research paper that a person signature's height is to width ratio always remains the same, hence
I computed this feature again open cv helped a lot, I had to make Contours to basically make a bounding rectangle around the signature.

<img src="https://i.imgur.com/OTlwmBc.png" alt="drawing"/> <br>

#### Other Features
Feature such as **skewness** , **kurtosis** and **standard deviation** were also used which have great
statistical relevance in image processing. I won't go into much details for them, [but here is some information](https://dsp.stackexchange.com/questions/30435/what-do-skewness-and-kurtosis-represent) regarding this.

### Architecture
The features which I am using are kinda specific to a person that is, they could identify the forgery of a specific person on compared to his/her genuine signature but they couldn't do this job in general
hence I ended up with *two models*.
#### First Model
This Model is a *Convolution neural network* , it's task is to classify the sample signature into its true class, here all the people (customers in case of banks) are treated as different classes, the CNN's task is to identify the class of the signature regardless of it being genuine or forged . For example, a bank has 2000 customers then there will be 2000 classes. In simple words CNNs task is to identify the person to which the signature belongs regardless of it being genuine or forged.
#### Second Model
After the class of the Signature is classified I trained another network which uses the handpicked features to predict the desired output by using **KNN classifier** , this classifier was trained only on the data of the particular person(or the class which was classified by the first model). For this, I made a number of data frames that is if there are 100 customers then 100 data frames each containing genuine as well forged as samples of that particular person.

### Conclusion
[follow this link for the GitHub repo of the project](https://github.com/piyush-98/Signature_Recogntion)<br>
The network gave about an accuracy of 85 % on the test set, which is quite considerable I guess. This whole work was done for an online competition though I didn't get through but it gave a lot of experience and I hereby apologize for all the spelling mistakes and grammatical errors I did throughout this blog, thanks for bearing.
