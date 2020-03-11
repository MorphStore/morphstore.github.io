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

In these systems, data compression already plays an important role. Aside from reducing the amount of data, compressed data offers several advantages such as less time spent on load and store instructions and a better utilization of the cache hierarchy. Moreover, a direct processing of the compressed data is possible in many cases. However, existing systems only provide a very limited set of compression algorithms for base data. Furthermore, during query processing, these systems only keep the data compressed until an operator cannot process the compressed data directly, whereupon the data is decompressed, but not recompressed. Thus, the full optimization potential is not exploited.

## Our Approach
To exploit this potential for an efficient OLAP query processing, we designed a novel columnar processing model with the following design principles: 
1. All generated intermediate results during query processing should be representable using a lightweight data compression algorithm. With that, we want to enable the *continuous* usage of compression for the whole query execution.  
2. Since data characteristics have an impact on the compression scheme decision and usually change during query processing, a suitable scheme should be chosen for each intermediate from a rich and easily extensible set of schemes. Moreover, the selection for each intermediate should not depend on the scheme used for another one to independently adapt to its particular data characteristics. This implies that a change of the compression scheme from one intermediate to the next should be possible in a very efficient and flexible way.
3. No physical columnar query operator should require the uncompressed materialization of its entire input or output data, since this would severely limit the benefits achievable through compression. In particular, a full decompression of the input data should be avoided.
4. To reduce the computational overhead for compression and decompression, our processing model heavily applies vectorization. On mainstream CPUs, this vectorization is done using SIMD extensions such as Intel’s SSE (Streaming SIMD extensions) or AVX (Advanced Vector Extensions). 

## News
2020-03-01 - We submitted our paper entitled "MorphStore: Analytical Query Engine with a Holistic Compression-Enabled Processing Model" to PVLDB. **Our [VLDB-2020](https://github.com/MorphStore/VLDB-2020) repository contains everything required to reproduce the experiments.**

2019-10-14 - Our paper "Hardware-Oblivious SIMD Parallelism for In-Memory Column-Stores" has been accepted at CIDR 2020.
