## Corrected code for Schönbrodt, F. D. & Perugini, M. (2013)
### “At what sample size do correlations stabilize?” [Journal of Research in Personality, 47, 609-612. doi:10.1016/j.jrp.2013.05.009]
### Link to [Corrigendum](https://osf.io/p2kag/)

The original code contained a bug in the r-to-Z conversion: A misplaced parenthesis had the effect that the r-to-Z conversion was *not* applied and that the width of the corridor of stability was defined in the r metric (not in the Z metric). Thanks to Dean Eckles and André Kretzschmar for reporting the bug. The updated code has a parameter in the `getPOS()` function which allows  to define the width of the corridor either in the r metric (`metric="r"`) or in the Z metric (`metric="Z"`). In the [correction to the paper](https://osf.io/p2kag/), we argue that staying in the r metric is actually a better aproach.

- Running `01-simdata.R` creates the simulated data sets, which then are saved to the `/simData` subfolder (the results from this computations have a size of 7GB and therefore cannot by synced to Github)
- Running `02-analyse.R` analyzes the simulated data sets in two steps:
	- (a) Find the point of stability for each trajectory (and three different widths of the corridor of stability) --> this results in a distribution of points of stability (POS). These distributions are saved as intermediate result files in subfolders `/POS` (for corridors in the r metric) and `POS_Z` (for corridors in the Z metric)
	- (b) Find the 80%, 90%, and 95% quantile of each POS distribution, print the table
- The (now reproducible) results are in `Results_r_metric.txt` (which reproduces the reported Table 1 in the original publication) and `Results_Z_metric.txt` (which produces the results if the r-to-Z conversion is applied).
	
Note: The original simulations from Schönbrodt & Perugini (2013) unfortunately did not use a seed; hence the originally reported results are not fully reproducible and the script here will produce slightly different results.

See the official correction here: XXX (to be updated)

## Results (with corridor in *r* metric)

This is a replication of the originally reported results:

```
  rho 0.8_0.1 0.8_0.15 0.8_0.2 0.9_0.1 0.9_0.15 0.9_0.2 0.95_0.1 0.95_0.15 0.95_0.2
1 0.1     252      111      62     360      159      89      474       210      117
2 0.2     238      105      59     341      150      84      448       198      111
3 0.3     215       95      52     308      136      75      405       178       99
4 0.4     183       81      45     263      116      64      347       153       86
5 0.5     145       63      35     209       92      52      276       122       69
6 0.6     105       46      26     152       68      38      203        91       52
7 0.7      66       29      20      96       44      25      129        60       36
```

## Results (with corridor in *Z* metric)


```
  rho 0.8_0.1 0.8_0.15 0.8_0.2 0.9_0.1 0.9_0.15 0.9_0.2 0.95_0.1 0.95_0.15 0.95_0.2
1 0.1     259      115      65     370      165      94      487       218      123
2 0.2     259      116      66     372      166      94      486       218      123
3 0.3     261      116      65     372      166      93      490       218      123
4 0.4     262      117      66     375      167      94      489       219      124
5 0.5     260      115      65     371      165      93      483       218      123
6 0.6     260      116      65     371      166      93      486       219      123
7 0.7     261      115      65     372      165      94      487       218      123
```
