![Version](https://img.shields.io/static/v1?label=dsd4xtals&message=0.3&color=brightcolor)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)


# Crystal improvement with Definitive Screening Designs (DSDs)

## Purpose
This repository contains Excel spreadsheets for applying Definitive Screening Designs (DSDs) to the size optimization of crystals of biological macromolecules (proteins and nucleic acids).
Bradley Jones and Christopher Nachtscheim developed DSDs ([Jones and Nachtscheim 2011](https://doi.org/10.1080/00224065.2011.11917841)).
Crystal size is generally proportional to its diffraction power, provided it is not internally disordered and is properly cryoprotected. 
Crystallographers seek large crystals to obtain high-resolution data for high-quality structures.

It takes about 3 minutes to edit a spreadsheet to customize it for a new crystallization experiment.
These spreadsheets ease the application of DSDs in laboratory experiments.
These spreadsheets could also be adapted to other laboratory and field experiments.
If you need a design with a run configuration different from a 4 x 6 array, please post an issue.

<p align="center"><img src="images/composite1.png" style="width: 90vw; min-width: 330px;"></p>


## Why DSDs?

DSDs are efficient designs for identifying the critical experimental factors that influence crystal size and other factors with little or no influence.
These designs are orthogonal and can detect the main effects and quadratic effects. 
These designs cannot detect higher-order interactions. 

DSDs are part of experimental screening designs, including the widely known fractional factorial designs.
Instead, we foresee DSDs being used after crystal leads have been found using sparse matrix crystallization screens or prior knowledge of the crystallization conditions for closely related proteins.
Reducing the number of factors to the vital few makes more efficient use of material and time during subsequent experiments.
These follow-up experiments optimize the levels of each vital factor to find the combination of factor levels that leads to the largest crystals.


## Contents of design library

This first set of designs is limited to testing three to 11 factors.
These designs can fit in a 24-well crystallization tray format.
We plan to make designs for a 96-well format for use with liquid-handling robots and crystallization robots.
Robots have the advantage of reduced experimental error due to more precise liquid handling.

There is one spreadsheet per design.
The user enters the factors' names, their central factor level, and the delta to set the low and high levels to be tested.
The user also enters the stock concentrations for chemical components; the spreadsheet autogenerates the volumes of each stock solution and water to be added to the crystallization solution.

<p align="center"><img src="images/FactorLevelInput.png" style="min-width: 110px;"></p>

A specific combination of factor levels are assigned to a particular crystallization well (an experimental `run' or `treatment' ) through the design matrix.
The design matrix is represented by the columns of codings (see below).
These codings have values of -1, 0, and +1 for continuous variables and -1 and 1 for categorical variables.
It is best to minimize the number of categorical variables because their presence complicates the analysis and weakens the power of the experiment. 

<p align="center"><img src="images/codings.png" style="min-width: 110px;"></p>

The assignment of the runs to the wells (see below) should be randomized upon each new use of the experimental design. 
Instructions on randomizing the runs' assignment to the wells are included in the spreadsheet.
A column of random numbers is used to randomize the assignment of treatments to wells.
After the rows are sorted based on the random numbers, a new set of random numbers is automatically generated and ready for use in another round of randomization.


<p align="center"><img src="images/wellsA.png" style="width: 90vw; min-width: 110px;"></p>

The results response that we seek to maximize is crystal size.
In my lab, we use the most extended length of the longest crystal.
This crystal is the one that is most apt to be cryo-protected successfully.
We record this information on a score sheet (see below) by date.


<p align="center"><img src="images/Scoresheet.png" style="min-width: 110px;"></p>



Alternatively, a 21-level scoring system can be used.
This scoring system does not require precise crystal length measurements and accounts for results that do not include crystals larger enough to have their lengths measured.
An example is shown below and is included in the spreadsheets.

<p align="center"><img src="images/Scores.png" style="min-width: 110px;"></p>


The spreadsheets are named according to the following key: 

- DSD code for the experimental design type
- r  number of runs
- C number of chemical factors
- P number of physical factors
- c number of categorical factors

To download the spreadsheets, git clone the repo or click on `code` in the green button in the upper right and select `Download zip` to download all of the files. Downloading a single Excel file is problematic. 

## Analysis of the results

Because the continuous factors have three levels, non-linear effects can be approximated with linear models that contain quadratic terms. 
These linear models can be applied using the response surface methodology.
These analysis tools are available through the R package `rsm` by Lenth (2009).


## References
Jones, B. and Nachtsheim, C. J. (2011) A Class of Three-Level Designs for Definitive Screening in the Presence of Second-Order Effects. Journal of Quality Technology, 43, 1-15.

Lenth, R.V. (2009) Response-Surface Methods in R, using rsm. Journal of Statistical Software, 32, 1–17.

## Update History

|Version      | Changes                                         | Date                 |
|:-----------:|:-----------------------------------------------:|:--------------------:|
| Version 0.2 |  Fixed typos in README.md                       | 2024 April 10        |
| Version 0.3 |  Fixed wording in README.md                       | 2025 April 7        |

## Sources of funding

- NIH: R01 CA242845
- NIH: R01 AI088011
- NIH: P30 CA225520 (PI: R. Mannel)
- NIH P20GM103640 and P30GM145423 (PI: A. West)
