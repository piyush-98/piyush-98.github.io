---
published: false
---
---
layout: post
title:  "Building ReverSEE"
date:   2018-08-02 +0530
categories: machinelearning project
---

## Building ReverSEE

This post aims to cover the developement process of [ReverSEE](https://github.com/arush15june/reversee), a reverse image search hoopla i built to essentialy learn to use PyTorch.

# a silly idea

**popular indian fashion website** allows you to throw a picture of a random tshirt in their search bar and they'll find you how a similar tshirt available in the store. 

**Idea**: How could i go about building something similar of my own? A Mini Reverse Image Search! Perfect oppurtunity to learn to use PyTorch 0.4.0, recently released on Windows, where with accidental CUDA 9.1 drivers, Tensorflow wouldn't run without building it from source, a task i refused to commit.

The basic architecture:

`Web Frontend <-- API --> Model` 

To fuel this idea with my limited skills in machine learning, I sought out to prepare a dataset of product images which would then be used to train a model, comparing an input image with th database with the most probable outputs be displayed on a webpage.

Quick google searches led me to the ideas of Siamese Networks, a kind of Convolutional Neural Networks, which could be trained and used for comparison, in this case, the tshirt database with an input image.

# The Dataset

Though, ReverSEE could be trained on a dataset of pretty much any product, I chose T-Shirts. Back to the popular indian fashion website, it has a client side rendered frontend, just like all modern websites, which means all the product data is procured by requesting an HTTP API using XML-HTTP Requests.

In the Network tab of the Chrome Developer Tools, filtering it to only display XHR, you could find out the API Endpoint used to get product data for a specific category, in this case, `Men's T-Shirts`. The endpoint was actually found out by a friend, [Ujjwal Gupta](https://github.com/slapbot).

With this endpoint we could request paginated tshirt data, a simple script, `model/scraper/scraper.py` to scrape this data was written which scraped around 10000 odd images of tshirts.

Although, after a lot of work had been done, It was found that there were a lot of duplicate images, around 2500 images, this was later fixed by a bash command/tool (WSL Bash runnning on Windows 10) which i have since lost. It removed duplicates based on their md5 hash. 7500~ pictures remain after this cleansing.

All of these pictures were downloaded at a high quality resolution of 1080x1440 pixels, later resized to 130x150 pixels using `model/scraper/resize.py` to be used for training the the model.

# The Model

Before beginning research on the internet on how I could compare two pictures using neural networks, My own idea of the model was to use a CNN to classify the input images as one of the output classes, the classes representing each picture in the database, with this structure we could ge the most probably class for an input image, this was later implemented too.  

Research a.k.a using google, led to different articles and papers,	
- [https://hackernoon.com/one-shot-learning-with-siamese-networks-in-pytorch-8ddaab10340e](https://hackernoon.com/one-shot-learning-with-siamese-networks-in-pytorch-8ddaab10340e)
- [https://arxiv.org/pdf/1703.02344](https://arxiv.org/pdf/1703.02344)
- [https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf](https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf)
    
Teaching me about Siamese Networks, using two identical convolutional neural networks to generate a parameter which could be used to infer similarity between two images. With my limited understanding of CNN's and Siamese Networks, I will refrain from any technincal comments regarding how the process is done but it is covered in [https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf](https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf) for the ones interested.