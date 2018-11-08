---
layout: page
title: Projects
group: navigation
order: 3
---
{% include JB/setup %}

# Projects

I build real learning systems that has been used in the real world.
Most of these projects are actively developed and maintained as open source package.
I am honored to work with many outstanding collaborators on these projects.

### TVM: An Automated End-to-End Optimizing Compiler for Deep Learning
TVM is an open deep learning compiler stack for CPUs, GPUs, and specialized accelerators. It aims to close the gap between the productivity-focused deep learning frameworks, and the performance- or efficiency-oriented hardware backends.

- [TVM Project Website](https://tvm.ai)

### XGBoost: Scalable Tree Boosting

XGBoost is an optimized distributed gradient boosting library designed to be highly **efficient**, **flexible** and **portable**. It implements machine learning algorithms under the Gradient Boosting framework. XGBoost provides a parallel tree boosting(also known as GBDT, GBM) that solve many data science problems in a fast and accurate way. XGBoost is used to **many machine learning challenges** and has been **deployed in production** environments.
You can use it in any of your favorite language including python, R, Julia, java, scala. The distributed version can be easily deployed on
Hadoop, MPI, SGE and more recently DataFlow frameworks(e.g. Flink and Spark)

Backgroun Story: I created XGBoost when doing research related to variants of tree boosting and cannot find a fast tree boosting package for my experiments. It then become part of my research in building scalable learning systems.

- [Tutorial on Tree Boosting](https://xgboost.readthedocs.io/en/latest/tutorials/model.html)
- [XGBoost Project Repo](https://github.com/dmlc/xgboost)

### MXNet: Efficient and Flexible Deep Learning

MXNet stands for ***mix*** and ***maximize***. The idea is to combine the power of declartive programming
together with imperative programming. In its core, a dynamic dependency scheduler that automatically parallelizes both symbolic and imperative operations on the fly. A graph optimization layer on top of that makes symbolic execution fast and memory efficient. The library is portable and lightweight, and it scales to multiple GPUs and multiple machines.

Background Story: MXNet starts as a combination of many deep learning project: CXXNet which I created together with Bing Xu, Minverva from NYU and Purine from NUS. We are later joined by Chiyuan who is the creator of Mocha.jl. This is a truely collaborative project that combines the wisdom from several deep learning projects and researchers from many different inistitute.

- [MXNet Paper on LearningSys](data/pdf/mxnet-learningsys.pdf)
- [Open Source Design Notes on Deep Learning Systems](http://mxnet.io/architecture/index.html)
- [MXNet Project Repo](https://github.com/dmlc/mxnet)


### MShadow:  A Unified CPU/GPU Matrix Template Library in C++/CUDA
MShadow is an efficient, device invariant and simple tensor library for machine learning project that aims for both simplicity and performance.
Basically, it allows you to write expressions and translate them to GPU code during compilation.
This is the backbone library behind many deep learning platforms, including MXNet, CXXNet and Apache Singa.

Background Story: I started to write CUDA code since my undergrad when doing my first deep learning project on restricted boltzmann machine.
As much as I liked hacking GPU, I hated the repeative effort on writing similar code over again.
Then we build this libary, with the power of template programming of C++, we are finally able to write ```weight += learning_rate * gradient``` :)

- [Introduction to Expression Template](https://github.com/dmlc/mshadow/tree/master/guide/exp-template/README.md) on how it works.
- [MShadow Project Repo](https://github.com/dmlc/rabit)

### DMLC-Core: Distributed Machine Learning Common Codebase
When you write distributed machine learning. There are many common non-trivial utility functions that you need.
Load the data from distributed filesystem in a sharded way; parse input file fast enough so your bigdata program
do not load too slowly; launch jobs on various environment; define and check parameters.
dmlc-core is the C++ library that solves all these common pains in distributed machine learning.

Background Story: It started when [Mu Li](http://www.cs.cmu.edu/~muli/) and I complained that we are doing the repeative jobs
when building distributed machine learning systems. "Why not work together to build these common parts together?"
So we get support from our advisors and created the library that backs many distributed learning systems, including MXNet and XGBoost.

- [DMLC-Core Project Repo](https://github.com/dmlc/dmlc-core)

### Rabit: Reliable Allreduce and Broadcast Interface
A light weight library that provides a fault tolerant interface of Allreduce and Broadcast for portable , scalable and reliable distributed machine learning programs. Rabit programs can run on various platforms such as Hadoop, MPI and Sun Grid Engine.
It backs the communication behind the Distributed XGBoost.
The newest version can also be used within DataFlow frameworks such as Flink and Spark.

Background Story: Rabit starts as a course project when I was taking on System Course at UW when we want to
build something related to machine learning. The original goal is simply to beat other frameworks.
Now it is to be able to port and run on all the frameworks :)

- [Rabit Project Repo](https://github.com/dmlc/rabit)

### SVDFeature: A Scalable and Flexible toolkit for collaborative filtering
This is a project I created when I was a M.S. at Shanghai Jiaotong University.
This project provides an abstract framework to build new matrix factorization variants simply by defining features.
This is the project that helped us to win two KDD Cups.

- [SVDFeature Project Home](http://svdfeature.apexlab.org)
