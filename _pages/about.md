---
permalink: /
title: "MorphStore - Analytical Query Engine"
excerpt: "About me"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

MorphStore is an in-memory columnar analytical query engine with a novel holistic compression-enabeld and highly-vectorized processing model.

## Motivation
With increasingly large amounts of data being collected in numerous application areas ranging from science to industry, the importance of online analytical processing (OLAP) workloads increases constantly. OLAP queries typically access a small number of columns, but a high number of rows and are, thus, most efficiently stored and processed by column-stores. Moreover, the significant developments in the main memory domain in recent years have rendered it possible to keep even large data sets entirely in main memory. For these reasons, in-memory column-store approaches have established themselves as state-of-the-art for OLAP workloads.

In these systems, compression algorithms already play an important role. Aside from reducing the amount of data, compressed data offers several advantages such as less time spent on load and store instructions and a better utilization of the cache hierarchy. Moreover, a direct processing of the compressed data is possible in many cases. However, existing systems only provide a very limited set of compression algorithms for base data. Furthermore, during query processing, these systems only keep the data compressed until an operator cannot process the compressed data directly, whereupon the data is decompressed, but not recompressed. Thus, the full optimization potential is not exploited.

## Our Approach


## News
2020-03-01 - We submitted our paper entitled "MorphStore: Analytical Query Engine with a Holistic Compression-Enabled Processing Model" to PVLDB. **Our [VLDB-2020](https://github.com/MorphStore/VLDB-2020) repository contains everything required to reproduce the experiments.**

2019-10-14 - Our paper "Hardware-Oblivious SIMD Parallelism for In-Memory Column-Stores" has been accepted at CIDR 2020.
