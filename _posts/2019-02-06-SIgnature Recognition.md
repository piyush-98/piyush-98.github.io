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

The **Right** image is the **genuine** signature and the **left** one is the **forged** one.
first problem was to remove the effects of different inks from the image as it can be of any form.
hence for that i applied thinning to the image by using morphological functions of sklearn.

here is the iamge after it.
<img src="https://i.imgur.com/JV5KaV9.png" alt="drawing" width="200"/>
