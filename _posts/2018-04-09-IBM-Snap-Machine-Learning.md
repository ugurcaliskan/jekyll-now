---
layout: post
title: IBM Snap Machine Learning Library
---

Snap Machine Learning Library, new kid on the block in the world of Machine Learning libraries. This time a team of researchers from IBM Research-Zurich developed a very promising ML library. In this post, I try to summarize basic properties of this library, for further detailed information please refer to the references section and especially the original research paper [3].

They briefly describe the system [2]; 
>"The library provides high-speed training of popular machine learning models on modern CPU/GPU computing systems and can be used to train models to find new and interesting patterns, or to retrain existing models at wire-speed (as fast as the network can support) as new data becomes available. This means less compute costs for users, less energy, more agile development and a faster time to result."

Brief Notes:

* New ML library from IBM Research.
* Developed in IBM Research Zurich.
* Efficient, scalable ML library that enables very fast training of generalized linear models.
* Main features are [1]; 
    * Distributed training
    * GPU acceleration
    * Sparse data structures
* System Description [1];
    * Data parallelism across worker nodes in a cluster
    * Parallelism across heterogeneous compute units within one worker node
    * Multi-core parallelism within individual compute units

The Research Team claims, the library allows more agile development, faster and more fine-grained exploration of the hyper-parameter spaces, enables scaling to massive datasets and makes frequent retraining of models possible in order to adapt to events.

## System Description

System implements several hierarchical levels of parallelism in order to partition the workload among different nodes in a cluster, take full advantage of accelerator units and exploit multi-core parallelism on the individual compute units [3]. They used 3 level parallelism;

1. Data parallelism across worker nodes in a cluster
2. Parallelism across heterogeneous compute units within one worker node.
3. Multi-Core parallelism within individual compute units.

They implement the system using several leading technologies. At the heart of their system is C++/CUDA library that implements the computational heavy and performance critical parts of the system in level 2 and level 3. The data-parallelism have been discussed using Spark and MPI.


## Benchmark

In benchmark, they use an online advertising dataset released by Criteo Labs (which has 4 billion training examples). Results were compared to Tensorflow on Google Cloud Platform.

Brief original benchmark results are below [2]:

<img src="https://github.com/ugurcaliskan/ugurcaliskan.github.io/raw/master/images/Criteo-Terabyte-Click-Logs-Benchmark-FINAL.001-524x1024.jpeg" alt="Original Benchmark Results" width="50%" height="50%" />

Please refer to the original blog post [2] for detailed benchmark results.

## Conclusions

World of ML libraries are fascinating and every day newly developed algorithms and libraries are joining this world. IBM Research latest attempt is very promising and worth to try in couple of cases. And it is also good idea to follow this teams research activities for further successful projects.

## References

1. [Snap Machine Learning - IBM Research Homepage](https://www.zurich.ibm.com/snapml/ "Snap Machine Learning Homepage")

2. Parnell, T and Dunner, C (2018, March 20). [IBM Sets Tera-scale Machine Learning Benchmark Record with POWER9 and NVIDIA GPUs; Available Soon in PowerAI ](https://www.ibm.com/blogs/research/2018/03/machine-learning-benchmark/ "Snap Machine Learning benchmark results"). [Blog post] Retrieved from https://www.ibm.com/blogs/research/2018/03/machine-learning-benchmark/

3. Dunner, C et all, [“Snap Machine Learning,” arXiv:1803.06333v1 [cs.LG]](https://arxiv.org/pdf/1803.06333.pdf), 16 Mar. 2018.
