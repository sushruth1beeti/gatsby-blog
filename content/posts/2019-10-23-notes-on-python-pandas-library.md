---
template: post
title: Notes On Python Pandas Library
slug: /pandas-notes
draft: true
date: 2019-10-23T04:39:34.957Z
description: >-
  This post is a detailed notes on Pandas,  an open-source Python Library
  providing high-performance data manipulation and analysis tool using its
  powerful data structures. The name Pandas is derived from the word Panel Data
  – an Econometrics from Multidimensional data.
category: python
tags:
  - python pandas
---
Pandas came into existence because of the need for data manipulation, analysis library, as plain python wouldn't cut it. Using Pandas, we can accomplish five typical steps in the processing and analysis of data, regardless of the origin of data — load, prepare, manipulate, model, and analyse.

There are three important data structures in pandas:

1. **Series:** As the name suggests it's a series of data, 1D labeled homogeneous array, which is size immutable.
2. **DataFrame:** General 2D labeled, size-mutable tabular structure with potentially heterogeneously typed columns.
3. **Panel:** General 3D labeled, size-mutable array. 

DataFrame is the most commonly used data structure in pandas, by using pandas manipulation of multi-dimensional matrices becomes easy.

To work data effectively in Python and pandas, we’ll need to read the csv file into a Pandas DataFrame. A DataFrame is a way to represent and work with tabular data — data that’s in table form, like a spreadsheet. Tabular data has rows and columns, just like our csv file, but it’ll be easier for us to read and sort through if we can view it as a table.

In order to read in the data, we’ll need to use the pandas.read_csv function. This function will take in a csv file and return a DataFrame. The below code will:

Import the pandas library. We rename it to pd so it’s faster to type out. This is a standard convention in data analysis and data science, and you will often see pandas imported as pd in other people’s code.

Once we read in a DataFrame, it’s helpful to take a look at what we’ve got in a more visual way. Conveniently, Pandas gives us two methods that make it fast to print out the data a table. These functions are:

DataFrame.head() — prints the first N rows of a DataFrame, where N is a number you pass as an argument to the function, i.e. DataFrame.head(7). If you don’t pass any argument, the default is 5.

DataFrame.tail() — prints the last N rows of a DataFrame. Again, the default is 5.

One of the big advantages of using Pandas over a similar Python package like NumPy is that Pandas allows us to have columns with different data types. In our data set, reviews, we have columns that store float values like score, string values like score_phrase, and integers like release_year, so using NumPy here would be difficult, but Pandas and Python handle it well.

Now that we’ve read the data in properly, let’s work on indexing reviews to get the rows and columns that we want.

Indexing DataFrames with Pandas

Earlier, we used the head method to print the first 5 rows of reviews. We could accomplish the same thing using the pandas.DataFrame.iloc method. The iloc method allows us to retrieve rows and columns by position. In order to do that, we’ll need to specify the positions of the rows that we want, and the positions of the columns that we want as well.
