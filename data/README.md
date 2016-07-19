# Data directory

Use this directory to navigate to your datasets of interest.

Each directory contains the following contents:

+ `best-datasets` — the 100 best datasets.
+ `best-datasets.tar.bz2` — the 100 best datasets in a single file for easy download.
+ `best-attributes.tsv` — specific attributes, such as association accuracies, for each of the best datasets.
+ `all-datasets` — additional content for each run (set), including attributes tracked over generations, and all the optimal datasets from the final generation.
+ `all-attributes.tsv` — specific attributes for each of the final datasets.

## Summary statistics for best datasets

For each attribute, the following table shows the average across the 100 best datasets. The `One-way(sd)` through `Five-Way(sd)` columns indicate the average accuracy of the top-performing MDR models: 0.5 represents random performance, while 1.0 represents perfect performance.

| n-way | HWE | One-way(sd) | Two-Way(sd) | Three-Way(sd) | Four-Way(sd) | Five-Way(sd) | name                         |
|-------|-----|-------------|-------------|---------------|--------------|--------------|------------------------------|
| Three | No  | .502(.001)  | .511(.007)  | .886(.023)    |              |              | [threeway](threeway)         |
| Three | Yes | .504(.002)  | .509(.003)  | .680(.024)    |              |              | [HWthreeway](HWthreeway)     |
| Four  | No  | .502(.001)  | .510(.003)  | ?             | .897(.018)   |              | [fourway](fourway)           |
| Four  | Yes | .507(.003)  | .513(.003)  | ?             | .673(.009)   |              | [HWfourway](HWfourway)       |
| Four  | No  | .501(.000)  | .504(.001)  | .518(.003)    | .567(.010)   |              | [fourwayNoLow](fourwayNoLow) |
| Five  | No  | .502(.001)  | .510(.002)  | ?             | ?            | .895(.009)   | [fiveway](fiveway)           |
| Five  | Yes | .511(.003)  | .518(.003)  | ?             | ?            | .693(.008)   | [HWfiveway](HWfiveway)       |
| Five  | No  | .503(.001)  | .508(.001)  | .518(.002)    | .543(.004)   | .690(.008)   | [fivewayNoLow](fivewayNoLow) |
