# Plate Randomization for Longitudinal Data/Samples
Wingerson, MJ
## Description
This project provides a structured method and tool for randomizing participant biological samples across plates or batches while numerically evaluating the balance of key participant covariates post-randomization. The goal is to mitigate batch effects commonly encountered in the analysis of biological samples. This project, developed with support from Patrick Carry and Carson Keeter, builds upon their existing [randomization scheme](https://github.com/carryp/PS-Batch-Effect) by including a longitudinal component. 

## Purpose 

## Methods

## Use example 

## Troubleshooting 

**Checking for outliers**
1. Visually using a histogram `plt.hist(x)`  
2. Through z-score conversion; $z>3.0$ could be concerning  
$z = \frac{x - \mu}{\sigma}$  
$x$ = individual value  
$\mu$ = mean of dataset  
$\sigma$ = standard deviation of dataset  
*Interpretation of z-scores: Subject data normalized to represent the number of standard deviations they are from the mean, where a value of 0 indicates 'exactly at the mean'* 
<br>

**Checking cumulative calibration graph**


<img src="figs/calibration_graph.png" alt="Calibration Graph" width="1000">

---
**Other notes for MJ**  
Neuro 4-plex (N4PA; GFAP, Tau, UCH-L1, NF-Light): 34 tests, 6-month shelf life
Cytokine 4-plex (Cyto 4P; IL1-Beta, IL-6, IL-10, TNF-Alpha): 34 tests, 12-month shelf life
BDNF: 68 tests across 2 plates, 6-month shelf life


<!--
![calibration graph](figs/calibration_graph.png)
-->
