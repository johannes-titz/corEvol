## Corrected code for Schönbrodt, F. D. & Perugini, M. (2013)
### “At what sample size do correlations stabilize?” [Journal of Research in Personality, 47, 609-612. doi:10.1016/j.jrp.2013.05.009]

The original code contained a bug in the r-to-Z conversion: A misplaced parenthesis had the effect that the r-to-Z conversion was *not* applied and that the width of the corridor of stability was defined in the r metric (not in the Z metric). The updated code has a parameter in the `getPOS()` function which allows  to define the width of the corridor either in the r metric (`metric="r"`) or in the Z metric (`metric="Z"`).

- Run 01-simdata.R to create the simulated data sets, which then are saved to the `/simData` subfolder (the results from this computations have a size of 7GB and therefore cannot by synced to Github)
- Run 02-analyse.R to analyze the simulated data sets in two steps:
	- (a) Find the point of stability for each trajectory (and three different widths of the corridor of stability) --> this results in a distribution of points of stability (POS). These distributions are saved as intermediate result files in subfolder `/POS` and `POS_Z`
	- (b) Find the 80%, 90%, and 95% quantile of each POS distribution
- The (now reproducible) results are in `Results_r_metric.txt` (which reproduces the reported Table 1 in the original publication) and `Results_Z_metric.txt` (which produces the results if the r-to-Z conversion is applied).
	

See the official correction here: XXX (to be updated)