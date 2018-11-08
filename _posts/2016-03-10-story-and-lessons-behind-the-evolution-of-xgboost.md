---
layout: page
title:  "Story and Lessons Behind the Evolution of XGBoost"
date:   2016-03-10 07:05:00 -0800
author: Tianqi Chen
---

## Introduction

I like large-scale machine learning and love to build scalable learning systems.
[XGBoost](http://dmlc.cs.washington.edu/xgboost.html) is one such project that
we created. It is **the package you want to use to solve your data-science problems**.
I might be a bit exaggerate, however, XGBoost indeed has been used by a series of kaggle winning solutions as
well as KDDCup winners. It is fast and optimized for out-of-core computations. You can use it for you data science problems,
as well as putting it as a part of production pipeline.

Recently, we published a detailed [**Paper** (XGBoost: A Scalable Tree Boosting System)](http://arxiv.org/abs/1603.02754) describing the improvements behind the magic.
In short, XGBoost **scale to billions of examples and use very few resources**.
In this blogpost, I would like to tell the story behind the development history of XGBoost and lessons I learnt.

## Beginning: Good Old LibSVM File

I created XGBoost when doing research on variants of tree boosting. It is a combination of boosted trees with conditional random field
and I find that there is no existing solution of tree boosters which satiesfies my need. So I decided to build my own.
The first version of xgboost looks like all my good old machine learning packages.
Write a configuration file, setup all the parameters, eat the libsvm file and off you go.

```bash
./xgboost config.conf data=trainData.libsvm
```

This was the way I used machine learning packages during my undergrads and it is still how many people(including me) using machine learning now.
Few people know about the package when I first put in on the github and I though it might lay there like some good old research repo code forever.

## Takeoff: Python, R and Kagglers

XGBoost starts to get popular when I decided try Higgs Boson Challenge at [Kaggle](https://www.kaggle.com/).
I am quite happy with my good old CLI version of xgboost and it surprisingly jumps on the 1st of the leaderboard.
My friend [Bing Xu](https://www.kaggle.com/binghsu) suggested me to publish the result and try to expose a python wrapper.
So we worked together to build one proptype, most of the API functions in python still remains the same today.
Later the R package is also added with the help of Tong He.

![](../../../data/img/xgboost-lang-stack.png)

XGBoost take off since then. Users like the python and R API a lot more than my favorite good old CLI program.
The reason can actually be explained by the above figure. **User can not be successful with xgboost alone**.
A data scientist need to combine the toolkits for data processing, feature engineering and machine learning together
to make innovations. Interfacing with R and python enables XGBoost to naturally work with language native data
pipelines and become much more powerful. It also enables easier customization and allow user to enhance the package to be more powerful.
There are a lot of exploration and visualization features in XGBoost now, which wouldn't be possible it stays as a CLI program.

## Don't be Isolated: Work with Scikit-Learn

XGBoost can never be successful alone. To make more exciting things happen, we need work together with other wonderful packages.
One such example is scikit-learn API. Thanks to the community contributors, XGBoost is now fully scikit-learn compatible.

![](../../../data/img/xgboost-pkg-stack.png)

It is quite common now for a user to directly use scikit-learn's grid search to find optimal parameters for XGBoost.
By defining clear common interface and embed into existing
ecosyste.  XGBoost is able to focus on scalibility, while also take benefit from other nice improvements in scikit-learn.
Same thing also happens in other languages as well.

## Summary of Lessons: Unix Philosophy in Machine Learning

XGBoost **focuses on one thing and does its best for you**.
In order to be useful for the users, XGBoost also have to **be open and integrate well with other systems by common interface**.
This is exactly the Unix philosophy applied to data science and machine learning.
While there is a trend to build monolithic platforms which claimed to solve all the problems,
there is always new problem like data processing, scalability and GPU computing to be solved.
We need good solutions to solve each problem well and combine them in a flexible way.

XGBoost was designed to be closed package that takes input and produces models in the beginning.
The XGBoost package today becomes fully designed to be embeded into any languages and existing platforms.
It is like a Lego brick, that can be combined with other bricks to create things that is much more fun than one toy.

## Push Further: Embed Distributed XGBoost into YARN and Dataflow

XGBoost has been doing quite well on a single machine, but why stop here? The optimizations we made in the single machine
version can directly carried on to a distributed version.
Distributed system is the place where portability is even harder, mainly because each distributed computing frameworks have its
own abstractions. The SVM implementation on Platform A will not run on another platform B.

![](../../../data/img/xgboost-platform-stack.png)

Can we take the same Lego XGBoost brick and plug it onto different distributed systems? The answer is yes.
We build a common Allreduce runtime called [Rabit](https://github.com/dmlc/rabit) and use it as a bridge to port to different systems.
Example of supported platforms include MPI, SGE and YARN.

We also want to take a step further, to **integrate distributed xgboost with existing data flow frameworks**.
With excellent work from [Nan Zhu](https://github.com/CodingCat), the incoming [XGBoost4J Package](https://github.com/dmlc/xgboost/tree/master/jvm-packages)
will be fully compatible with all the dataflow pipelines in JVM stack, including Apache Flink and Spark.

## Summary
XGBoost evolves from the single CLI program to a package that can be used in **most the major languages and
distributed platforms**. You can checkout [XGBoost Resource page](https://github.com/dmlc/xgboost/blob/master/demo/README.md) for more resources.
XGBoost's success is not only due to its scalablity, but also due to its openness and portablity.
This is actually a success of the entire machine learning and data science ecosystem.

## Acknowledgement
All these could not happen without wonderful community of data scientists and machine learning researchers in XGBoost community.
