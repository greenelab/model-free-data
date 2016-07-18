# Case-control genetics datasets evolved to be epistatic

This repository contains the data for the following two studies:

1. [**Evolving hard problems: Generating human genetics datasets with a complex etiology**](https://doi.org/b44mk9)<br>
Daniel S. Himmelstein, Casey S. Greene, Jason H. Moore<br>
_BioData Mining_ (2011) DOI: 10.1186/1756-0381-4-21

2. [**A Model Free Method to Generate Human Genetics Datasets with Complex Gene-Disease Relationships**](https://doi.org/czh822)<br>
Casey S. Greene, Daniel S. Himmelstein, Jason H. Moore<br>
_Evolutionary Computation, Machine Learning and Data Mining in Bioinformatics_ (2010) DOI: 10.1007/978-3-642-12211-8_7

Previously, this data was hosted at http://discovery.dartmouth.edu/model_free_data/. As of July 2016, this repository is the preferred location as the legacy site is no longer supported.

## Introduction

This repository contains genetics datasets simulated to be complex. Each dataset contains 3,000 observations (rows), which represent samples/subjects for a genetic association study. Subjects are classified as cases (i.e. diseased when `Class` column is `1`) or controls (i.e. healthy when `Class` column is `0`). The remaining columns (e.g. `X1`, `X2`, `X3`) represent biallelic SNPs and are coded as `0` for homozygous, `1` for heterozygous, and `2` for homozygous of the alternate allele. Datasets were created with 3, 4, and 5 SNPs. For example, a subset of a 5 SNP dataset looks like:

| X1 | X2 | X3 | X4 | X5 | Class |
|----|----|----|----|----|-------|
| 0  | 1  | 1  | 1  | 1  | 0     |
| 0  | 0  | 0  | 1  | 0  | 0     |
| 2  | 1  | 1  | 2  | 0  | 0     |
| 1  | 1  | 0  | 1  | 0  | 1     |
| 1  | 1  | 1  | 1  | 2  | 1     |
| 1  | 2  | 2  | 0  | 0  | 1     |

Datasets were created using an evolution strategy. Each run used a population size of 1,000 (number of datasets) and evolved for 2,000 generations. Each generation consisted of introducing mutations and selecting to survive datasets that were optimal for at least one attribute. Only the datasets from the final generation of a run were retained. From the 2,000 final datasets yielded by a run, a single "best" dataset was chosen.

We created datasets with following attributes:

+ **n-way**: the number of SNPs in the dataset, ranging from 3–5. The joint-predictiveness of all SNPs was maximized, while the predictiveness of lower order SNP-combinations was minimized.
+ **NoLow**. All runs were optimized for having no one-way (marginal) or two-way (pairwise epistatic) associations. NoLow refers to whether, in addition to minimizing 1 and 2-way effects, all lower order effects were minimized. For example, `fivewayNoLow` maximized the 5-way effect, while minimizing 1, 2, 3, and 4-way effects.
+ **HWE**: whether SNPs were optimized to maintain Hardy-Weinberg equilibrium.

In total, eight types of datasets were created, which combined the attributes above. For each dataset type, 100 runs were performed resulting in 100 best datasets per type.

## Best datasets

Most users will be interested in only the best datasets, since multiple datasets from the same run may not be independent. The following table shows the average attributes of best datasets. The `One-way(sd)` through `Five-Way(sd)` columns indicate the average accuracy of the top-performing MDR models: 0.5 represents random performance, while 1.0 represents perfect performance.

| n-way | HWE | One-way(sd) | Two-Way(sd) | Three-Way(sd) | Four-Way(sd) | Five-Way(sd) | name       |
|-------|-----|-------------|-------------|---------------|--------------|--------------|-------------------|
| Three | No  | .502(.001)  | .511(.007)  | .886(.023)    |              |              | threewayBests     |
| Three | Yes | .504(.002)  | .509(.003)  | .680(.024)    |              |              | HWthreewayBests   |
| Four  | No  | .502(.001)  | .510(.003)  | -             | .897(.018)   |              | fourwayBests      |
| Four  | Yes | .507(.003)  | .513(.003)  | -             | .673(.009)   |              | HWfourwayBests    |
| Four  | No  | .501(.000)  | .504(.001)  | .518(.003)    | .567(.010)   |              | fourwayNoLowBests |
| Five  | No  | .502(.001)  | .510(.002)  | -             | -            | .895(.009)   | fivewayBests      |
| Five  | Yes | .511(.003)  | .518(.003)  | -             | -            | .693(.008)   | HWfivewayBests    |
| Five  | No  | .503(.001)  | .508(.001)  | .518(.002)    | .543(.004)   | .690(.008)   | fivewayNoLowBests |

## License

No rights reserved. This repository including its datasets are released under the CC0 Public Domain Dedication (see [`LICENSE.md`](LICENSE.md)).
