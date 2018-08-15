# Case-control genetics datasets evolved to be epistatic

This repository contains the data for the following two studies:

1. [**Evolving hard problems: Generating human genetics datasets with a complex etiology**](https://doi.org/b44mk9) (_Prefered Citation_)<br>
Daniel S. Himmelstein, Casey S. Greene, Jason H. Moore<br>
_BioData Mining_ (2011) DOI: 10.1186/1756-0381-4-21 · PMID: 21736753 · PMCID: PMC3154150<br>


2. [**A Model Free Method to Generate Human Genetics Datasets with Complex Gene-Disease Relationships**](https://doi.org/czh822)<br>
Casey S. Greene, Daniel S. Himmelstein, Jason H. Moore<br>
_Evolutionary Computation, Machine Learning and Data Mining in Bioinformatics_ (2010) DOI: 10.1007/978-3-642-12211-8_7

Previously, this data was hosted at http://discovery.dartmouth.edu/model_free_data/. In July 2016, the data was migrated to this repository and modernized. The legacy site is no longer supported, use this site instead. The data contents are equivalent, although directory structures, file extensions, and text-file header rows have been refined.

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

Datasets were created using an evolution strategy. Each run used a population size of 1,000 (number of datasets) and evolved for 2,000 generations. Each generation consisted of introducing mutations and selecting to survive datasets that were optimal for at least one attribute. Only the Pareto-optimal datasets from the final generation of a run were retained. From the Pareto-optimal datasets yielded by a run, a single "best" dataset was chosen.

We created datasets with following attributes:

+ **n-way**: the number of SNPs in the dataset, ranging from 3–5. The joint-predictiveness of all SNPs was maximized, while the predictiveness of lower order SNP-combinations was minimized.
+ **NoLow**. All runs were optimized for having no one-way (marginal) or two-way (pairwise epistatic) associations. NoLow refers to whether, in addition to minimizing 1 and 2-way effects, all lower order effects were minimized. For example, `fivewayNoLow` maximized the 5-way effect, while minimizing 1, 2, 3, and 4-way effects.
+ **HWE**: whether SNPs were optimized to maintain Hardy-Weinberg equilibrium.

In total, eight types of datasets were created, which combined the attributes above. For each dataset type, 100 runs were performed resulting in 100 best datasets per type. Most users will be interested in only the best datasets, since multiple datasets from the same run (set) may not be independent.

## Access datasets

The following table links to repository location with the datasets for a given attribute combination. SNPs refers to the number of SNPs in each dataset. 1-Way through 5-Way indicate whether associations of that order exist: No means datasets were evolved _not to have_ that effect; Yes means datasets were evolved _to have_ that effect; and Possibly means datasets were not optimized for that effect.

| SNPs | 1-Way | 2-Way | 3-Way    | 4-Way    | 5-Way | HWE | Name                              |
|------|-------|-------|----------|----------|-------|-----|-----------------------------------|
| 3    | No    | No    | Yes      |          |       | No  | [threeway](data/threeway)         |
| 3    | No    | No    | Yes      |          |       | Yes | [HWthreeway](data/HWthreeway)     |
| 4    | No    | No    | Possibly | Yes      |       | No  | [fourway](data/fourway)           |
| 4    | No    | No    | Possibly | Yes      |       | Yes | [HWfourway](data/HWfourway)       |
| 4    | No    | No    | No       | Yes      |       | No  | [fourwayNoLow](data/fourwayNoLow) |
| 5    | No    | No    | Possibly | Possibly | Yes   | No  | [fiveway](data/fiveway)           |
| 5    | No    | No    | Possibly | Possibly | Yes   | Yes | [HWfiveway](data/HWfiveway)       |
| 5    | No    | No    | No       | No       | Yes   | No  | [fivewayNoLow](data/fivewayNoLow) |

## Need help?

If you have any questions or feedback, please submit an [Issue on GitHub](https://github.com/greenelab/model-free-data/issues "Issues for greenelab/model-free-data").

## License

No rights reserved. This repository including its datasets are released under the CC0 Public Domain Dedication (see [`LICENSE.md`](LICENSE.md)).
