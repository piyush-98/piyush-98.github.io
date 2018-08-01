---
published: false
---
---
layout: post
title:  "Building ReverSEE"
date:   2018-08-02
categories: machinelearning project
---

## Building ReverSEE

This post aims to cover the developement process of [ReverSEE](https://github.com/arush15june/reversee), a reverse image search hoopla i built to essentialy learn to use PyTorch.

# a silly idea

**popular indian fashion website** allows you to throw a picture of a random tshirt in their search bar and they'll find you how a similar tshirt available in the store. 

**Idea**: How could i go about building something similar of my own? A Mini Reverse Image Search! Perfect oppurtunity to learn to use PyTorch 0.4.0, recently released on Windows, where with accidental CUDA 9.1 drivers, Tensorflow wouldn't run without building it from source, a task i refused to commit.

The basic architecture:

`Web Frontend <-- API --> Model` 


# The Dataset

Though, ReverSEE could be trained on a dataset of pretty much any product, I chose T-Shirts. Back to the popular indian fashion website, it has a client side rendered frontend, just like all modern websites, which means all the product data is procured by requesting an HTTP API using XML-HTTP Requests.

In the Network tab of the Chrome Developer Tools, filtering it to only display XHR, you could find out the API Endpoint used to get product data for a specific category, in this case, `Men's T-Shirts`. The endpoint was actually found out by a friend, [Ujjwal Gupta](https://github.com/slapbot).

With this endpoint we could request paginated tshirt data, a simple script to scrape this data was written which scraped around 8000 odd images of tshirts.
