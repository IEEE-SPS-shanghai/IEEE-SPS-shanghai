layout: '[layout]'
title: 基于特征融合的行人再识别
date: 2017-01-05 17:10:18
tags: [毕设]
categories: 笔记
---

A FEATURE FUSION STRATEGY FOR PERSON RE-IDENTIFICATION 

<!--more-->



## 需要用到的算法

### Low-level Weighted Histograms of Overlapping Stripes (WHOS) features

> WHOS = [HS,RGB,HOG]

> HS and RGB are part-based color histograms in different color spaces that can compensate each other against illumination changes. HOG is a global feature which is proven to be effective in pedestrian related task.

###  Mid-level colorname descriptors

> There are 11 pre-defined colors (**black, blue, brown, grey, green, orange, pink, purple, red, white and yellow**)

###  KISSME algorithm

***

## 实验步骤 

### 预处理 【Pre-processing】

> 由两部分组成： per-son segmentation and body part subdivision.

> **Person segmentation**：dividing original 8 body parts parsing to only 2 parts parsing i.e. **foreground and background**. The masks after background removal are then used on   original images to generate pedestrian silhouettes. 

> **Body part subdivision**：The part-based body models used in current appearance descriptors can be divided into three categories: fixed, adaptive and learned models. Fixed models, in which the sizes and positions of body parts are chosen a-priori, are simple yet proven to be effective in many pedestrian related tasks. We utilized a fixed part model in our approach that divides each pedestrian image into **six horizontal stripes** of equal size.


###  【Global color name descriptor】
> Then the global color name descriptor can be obtained as a **66-dimension ( six horizontal stripes × 11 pre-defined colors )** feature vector by concatenating each stripe’s CN features. We then use **PCA** to reduce the dimension to ***m*** (for different datasets we use different number because the number of persons varies in different datasets).

### 【Combined feature representation】

>  *WHOS = [HS,RGB,HOG]*

> The dimension of WHOS is 2960 in original representation, we use PCA to reduce the dimension to ***n*** (for different datasets we use different number because person number varies in different datasets) because the original demension may be too high.


> *F = [CN,WHOS]*

> Our combined feature representation is then a (***m+n***) dimension (varies in different datasets) feature vector by fusing mid-level CN and low-level WHOS. WHOS are high-dimension low-level features.After fusion, PCA is adaopted to reduce the dimension if necessary.

### 【person matching】

- Mahalanobis distance 

- KISSME



### 【Experiments on several public person re-identification datasets (VIPeR, i-LIDS and CAVIAR4REID)】





***

