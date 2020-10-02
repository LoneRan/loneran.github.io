---
layout: post
date: 2020-10-01 19:59
title:  "Cassandra in Java"
description: 
comments: true
category: 
- docs
- help
tags:
- NoSQL
- Casssandie
- Jaca
---

> This tutorial is an introductory guide to the Apache Cassandra database using Java.

## Apache Cassandra

>what do you know about Cassandra?

Cassandra is a scalable NoSQL database that provides continuous availability with no single point of failure and gives the ability to handle large amounts of data with exceptional performance.

This database uses a **ring design** instead of using a **master-slave architecture**. In the ring design, there is no master node – all participating nodes are identical and communicate with each other as peers.

This makes Cassandra a horizontally scalable system by allowing for the incremental addition of nodes without needing reconfiguration.

### Key Concepts
- **Cluster**: a collection of nodes or Data Centers arranged in a ring architecture. A name must be assigned to every cluster, which will subsequently be used by the participating nodes
- **Keyspace**: If you are coming from a relational database, then the schema is the respective keyspace in Cassandra. The keyspace is the outermost container for data in Cassandra. The main attributes to set per keyspace are the Replication Factor, the Replica Placement Strategy and the Column Families
- **Column** Family: Column Families in Cassandra are like tables in Relational Databases. Each Column Family contains a collection of rows which are represented by a Map<RowKey, SortedMap<ColumnKey, ColumnValue>>. The key gives the ability to access related data together
- **Column**: A column in Cassandra is a data structure which contains a column name, a value and a timestamp. The columns and the number of columns in each row may vary in contrast with a relational database where data are well structured
