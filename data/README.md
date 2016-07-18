## Summary statistics for best datasets

For each attribute, the following table shows the average across the 100 best datasets. The `One-way(sd)` through `Five-Way(sd)` columns indicate the average accuracy of the top-performing MDR models: 0.5 represents random performance, while 1.0 represents perfect performance.

| n-way | HWE | One-way(sd) | Two-Way(sd) | Three-Way(sd) | Four-Way(sd) | Five-Way(sd) | name         |
|-------|-----|-------------|-------------|---------------|--------------|--------------|--------------|
| Three | No  | .502(.001)  | .511(.007)  | .886(.023)    |              |              | threeway     |
| Three | Yes | .504(.002)  | .509(.003)  | .680(.024)    |              |              | HWthreeway   |
| Four  | No  | .502(.001)  | .510(.003)  | ?             | .897(.018)   |              | fourway      |
| Four  | Yes | .507(.003)  | .513(.003)  | ?             | .673(.009)   |              | HWfourway    |
| Four  | No  | .501(.000)  | .504(.001)  | .518(.003)    | .567(.010)   |              | fourwayNoLow |
| Five  | No  | .502(.001)  | .510(.002)  | ?             | ?            | .895(.009)   | fiveway      |
| Five  | Yes | .511(.003)  | .518(.003)  | ?             | ?            | .693(.008)   | HWfiveway    |
| Five  | No  | .503(.001)  | .508(.001)  | .518(.002)    | .543(.004)   | .690(.008)   | fivewayNoLow |
