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

A recommender system has to decide between two methods for information delivery when providing the user with recommendations:

**Exploitation:** The system chooses documents similar to those for which the user has already expressed a preference.

**Exploration:** The system chooses documents where the user profile does not provide evidence to predict the user’s reaction.

Most recommender systems focus on the task of information filtering, which deals with the delivery of items selected from a large collection that the user is likely to find interesting or useful. Recommender systems are special types of information filtering systems that suggest items to users. 

Talking technically, information filtering can be divided into three types:

* **Content Based Filtering:** Content-based filtering selects items based on the similarities between the content description of an item and the user’s preferences
* **Collaborative Filtering:** Collaborative filtering select items based on the similarities between the preferences of different users
* **Hybrid Filtering:** A hybrid approach, combining collaborative filtering and content-based filtering also exists.

We'll talk about all these filtering methods more in detail.

**Content Based Filtering:**

Given user preferences for items, recommend similar items based on a domain-specific notion of item content. This approach also extends naturally to cases where item metadata is available (e.g., movie stars, book authors, and music genres).

A content-based recommender works with data that the user provides, either explicitly (rating) or implicitly (clicking on a link). Based on that data, a user profile is generated, which is then used to make suggestions to the user. As the user provides more inputs or takes actions on those recommendations, the engine becomes more and more accurate.

**Advantages of Content Based Filtering**

**User** **independence**: Collaborative filtering needs other users’ ratings to find similarities between the users and then give suggestions. Instead, the content-based method only has to analyse the items and a single user’s profile for the recommendation, which makes the process less cumbersome. Content-based filtering would thus produce more reliable results with fewer users in the system.

**Transparency**: Collaborative filtering gives recommendations based on other unknown users who have the same taste as a given user, but with content-based filtering items are recommended on a feature-level basis.

**No cold start**: As opposed to collaborative filtering, new items can be suggested before being rated by a substantial number of users.

**Disadvantages of Content Based Filtering**

**Limited content analysis:** If the content doesn’t contain enough information to discriminate the items precisely, the recommendation itself risks being imprecise.

**Over-specialization:** Content-based filtering provides a limited degree of novelty, since it has to match up the features of a user’s profile with available items. In the case of item-based filtering, only item profiles are created and users are suggested items similar to what they rate or search for, instead of their past history. A perfect content-based filtering system may suggest nothing unexpected or surprising.
