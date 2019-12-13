---
template: post
title: Recommender Systems
slug: /recommender-systems
draft: true
date: 2019-12-13T05:31:09.695Z
description: >-
  Recommender Systems have become an integral part to many internet businesses.
  Percentage of users preferring recommendations have been increasing in the
  e-commerce world. In this blog, we go through some of the titbits about
  recommender systems. 
category: 'Machine Learning, Data Mining'
tags:
  - Machine Learning
  - Data Mining
  - Recommender Systems
---
I was working on a project for an e-commerce company, where we need to suggest users, products that go with other for the products they might be currently viewing or added into the cart. Something like _Amazon's Frequently Bought Together Section._

![frequently bought together](/media/frequently-bought-together.png "Frequently Bought Together in Amazon")

In layman terms, recommendations can be broadly divided into two types in e-commerce: 

* **Substitute Product Recommendations:** Recommending products that are similar to the product of interest.
* **Complimentary** **Product** **Recommendations:** Recommending products that go well with product of interest. Strategy here is to increase cross-sales.

Most recommender systems focus on the task of information filtering, which deals with the delivery of items selected from a large collection that the user is likely to find interesting or useful. Recommender systems are special types of information filtering systems that suggest items to users. 

Talking technically, information filtering can be divided into three types:

* **Content Based Filtering:** Content-based filtering selects items based on the similarities between the content description of an item and the user’s preferences
* **Collaborative Filtering:** Collaborative filtering select items based on the similarities between the preferences of different users
* **Hybrid Filtering:** A hybrid approach, combining collaborative filtering and content-based filtering also exists.
