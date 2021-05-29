---
title: Machine Learning Overview
date: 2020-02-08
tags: 
	- Machine Learning
	- NYU
	- Artificial Intelligence
categories: 
	- Computer Science
	- Machine Learning
mathjax: true
---

This notes is based on the class Machine Learning in Finance of NYU MFE, including basic knowledge of supervised learning.

# Supervised Learning

## Definition

The goal is to use the inputs to predict the values of the outputs. This exercise is called supervised learning.

## variables

inputs: predictors, independent variables,which are measured or preset.

output: responses, dependent variables

### variable types

+ quantitative / continuous variables
+ categorical / discrete variables / factors /
  + qualitative
  + dummy variables 

+ ordered categorical

## Algorithm

### k-Nearest Neighbors

### Linear Regression

### Logistic Regression

### Support Vector Machines

### Decision Trees and Random Forests

### Neural Networks

# Unsupervised Learning

## Algorithm

### k-means

### Hierarchical Cluster Analysis

### Expectation Maximization

### Principal Component Analysis

### Locally-Linear Embedding

### t-distributed Stochastic Neighbor Embedding

# Steps for a ML project

## Overview

### Frame the problem

### Data Understanding

+ descriptive statistics
+ relationship between independent and dependent variables (graphs)

### Data Cleaning

+ missing values
  + filling: filling n.a.
  + delete: drop n.a.

+ feature engineering
  + abstract feature 
  + select feature 

### Machine Learning Model

+ split training and testing
+ algorithm

### Evaluate Model

+ score
+ cross validation