# Bayesian Adaptive Regression Splines (BARS)
This repository hosts a Matlab version of Bayesian Adaptive Regression Splines for Matlab, which is currently in danger of being lost. Currently, the once freely available code is no longer hosted. This repo aims to mitigate this. Please note that the Matlab version only allows for Poisson prior distributions for now. The R version (found here: https://www.stat.cmu.edu/~kass/bars/bars.html) allows for both Poisson and Normally distributed priors. The Poisson distribution, being Poisson, is particularly useful for neural spikes and similar arrival events. For theory and implementation, see the following papers:

Dimatteo, I., Genovese, C.R., and Kass, R.E. (2001, Biometrika) Bayesian Curve-Fitting with Free-Knot Splines

Wallstrom, G., Liebner, J., and Kass, R.E. (2008, Journal of Statistical Software) An Implementation of Bayesian Adaptive
Regression Splines (BARS) in C with S and R Wrappers 

Behseta, S. and Kass, R.E. (2005, Statistics in Medicine) Testing equality of several functions: Analysis of single-unit
firing-rate curves across multiple experimental conditions

# Compiling Mex File
To run BARS in matlab, nlsd.mex needs to be compiled. Do so first by running in Matlab:
```
mex nlsd_mex.c
```
Successful completion will produce a nlsd_mex.mexw64 file in the current working directory.

# Example Usage
```
load example.data               %Needs to be done this way, example.data is a little finicky 
fit1 = barsP(example(:,2),[example(1,1) example(end,1)],60);       %Simple fit with defaults
% Parameters can be changed by accessing the default parameters structure and changing parameter values using standard Matlab dot notation.
bp = defaultParams;
bp.prior_id = 'POISSON';
bp.dparams = 4;
fit2 = barsP(example(:,2),[example(1,1) example(end,1)],60,bp);
```
Parameter data can be found the the J. Statistical Software Paper listed above.

# An example of BARS in experimental data.
I have successfully used BARS in my work (Characterization and closed-loop control of infrared thalamocortical stimulation produces spatially constrained single-unit responses. PNAS Nexus 3(2):pgae082 DOI: https://doi.org/10.1093/pnasnexus/pgae082) with a figure reproduced below:
![alt text](https://github.com/bscoventry/Bayesian-Adaptive-Regression-Splines/blob/main/BarsExample.png?raw=true)
