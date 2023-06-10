# Hadoop

Apache Hadoop is an open-source software framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. Hadoop was designed to scale up from a single server to thousands of machines, each offering local computation and storage. It is based on the MapReduce programming model and was initially created to support distribution for the Nutch search engine project.

Hadoop has two main components:

1. Hadoop Distributed File System (HDFS): This is the storage component of Hadoop, which splits large data files into blocks and stores them across a cluster of computers. Each block is replicated across multiple nodes to ensure the resilience of the system in case of node failure.

2. Hadoop MapReduce: This is the processing component, which provides a programming model for processing large sets of data in parallel. MapReduce jobs are divided into map and reduce phases. The map phase processes input data into intermediate key-value pairs, which are then processed by the reduce phase to generate output data.

In addition to these core components, Hadoop also has additional modules like Hadoop YARN (Yet Another Resource Negotiator) for job scheduling and cluster resource management, and Hadoop Common, which provides the Java libraries and utilities needed by other Hadoop modules.

The main advantage of Hadoop is that it allows for the processing of large amounts of data, in a distributed manner, on commodity hardware. This means that you don't need expensive, high-end hardware to process your data. Furthermore, the data processing is carried out locally on the nodes where the data is stored, reducing data transfer times and increasing processing speed.
