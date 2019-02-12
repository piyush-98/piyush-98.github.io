---
published: true
title: Signature Recognition
date: 2019-02-06T00:00:00.000Z
tags: AI model predict genuine forged Signature
categories: project
future: true
---
## Signature Recognition
The post is written about an AI model which can predict the forgery and  genuineness of a Signature sample . <br>

## Problem Statement
In organizations like banks where the Authenticity of the signature of a person is very important , there still doesn't exist any autonomous system which can predict frorgery of a signature .

Artificial Intelligence is the field of computer science that emphasizes on creating intelligent systems and through which
a machine can learn making decisions , I have been working in this field for a while ,so i decided to solve this problem with the help of some knowledge that i have been able gain in past few years.

## The Idea



In organizations like banks , they basically have the database of every customer hence i made my model accordingly .
So let's dive into the technicalities now .
### Dataset ---
I used various Online datasets available for the model . The idea was to having number of samples of every of person/customer including genuine as well as frorged signatures to make a `person dependent system`.
luckily i found various online datasets of the same manner online.I used dutch as well as english signatures so as to increase the dataset


### Preprocessing --
<img src="https://i.imgur.com/OUDPlgG.png" alt="drawing" width="200"/><img src="https://i.imgur.com/S6c5Uei.png" alt="drawing" width="200"/>

The **Right** image is the *genuine* signature and the **left** one is the *forged* one.

first problem was to remove the effects of different inks from the image as it can be of any form.
hence for that i applied *thinning* to the image by using `morphological functions of sklearn`.

<img src="https://i.imgur.com/JV5KaV9.png" alt="drawing" width="200"/>

`here is the image after thinning it` .

The image was also converted to *grayscale* from RGB and was also *normalized* to negate factors which
could affect the model, every image was also resized to same size i.e [50,100].
Image Preprocessing is one of the important task in deep learning specially in a task like signature
Recognition where small variations can truely affect the model.

### Features Extraction
As this task is not just recognizing dogs or cats or any other classification task , I had to extract
some hand picked features from the image , here i took help form some research papers i read
beforehand.

### Density of the signature
The Features tells us the ratio of number of pixels of the signature to the total number of image pixels, for this the image was binary segmented by open cv after converting it to grayscale.

### Compute the number of spatial symbols within the signature Image.
Every person in their signature uses some spatial symbols, such as they uses some ‘x’ marks (cross marks), star marks or
other symbols. The total number of spatial symbols of a person’s signature is unique. For calculating the total number of spatial symbols in a signature image we have to preprocess the image upto thinning. Then If we find that one pixel having
more than two neighbors each of which get the values 1 then those pixels will form a Spatial symbol

### Height/width ratio of the signature
I read in a research paper that a person's signature's height is to width ratio always remains the same , hence
i computed this feature again open cv helped a lot i had to make Contours to basically make a bounding rectangle around the signature.

### Kurtosis
