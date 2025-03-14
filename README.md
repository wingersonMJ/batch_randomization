# Plate Randomization for Longitudinal Data/Samples
Wingerson, MJ
## Description
This project provides a structured method and tool for randomizing participant biological samples across plates or batches while numerically evaluating the balance of key participant covariates post-randomization. The goal is to mitigate batch effects commonly encountered in the analysis of biological samples. This project, developed with support from Patrick Carry and Carson Keeter, builds upon their existing [randomization scheme](https://github.com/carryp/PS-Batch-Effect) by including a longitudinal component. 

## Purpose 
Collection of biological samples, such as blood plasma or serum, are beneficial for objectively measuring physiological responses to injury and rehabilitation. However, processing, long-term storage, and analysis are wraught with opportunities to introduce bias into your results (see [Troubleshooting](#troubleshooting) below for a list of things that can go wrong)

## How it works  

## Use example 

# Troubleshooting 

**Checking for outliers**
1. Visually using a histogram `plt.hist(x)`  
2. Through z-score conversion; $z>3.0$ could be concerning  
$z = \frac{x - \mu}{\sigma}$  
$x$ = individual value  
$\mu$ = mean of dataset  
$\sigma$ = standard deviation of dataset  
*Interpretation of z-scores:* Subject data normalized to represent the number of standard deviations they are from the mean, where a value of 0 indicates 'exactly at the mean'
<br>

**Checking cumulative calibration graph**  
<br>
The calibration graph plots the known value for the calibrators on the x-axis and the value estimated by SIMOA on the y-axis.  
This linear or non-linear relationship is used to 'calibrate', or fit/adjust, the actual participant values to reduce measurement error.

<img src="figs/calibration_graph.jpg" alt="Calibration Graph" width="1000">

Lower and higher values are usually squashed, or level off, because the SIMOA fails to accurately measure high and low concentrations.  
If outliers exist, check if their absolute values exist in squashed regions of the calibration graph.
<br>
<br>

**Checking values for samples run in multiple reps**  
<br>
*Run in multiple reps:* Some samples will be analyzed more than once by the SIMOA. For example, BDNF is run in 2 reps. This means you will have two BDNF concentration values for each sample. You use the mean of those values in the analysis, but a SD can also be calculated for that individual sample.  
| Subject ID   | Concentration Rep #1  | Concentration Rep #2  | Mean Concentration | Standard Deviation |
| ------------ | --------------------- | --------------------- | ------------------ | ------------------ |
| 001          | 0.85                  | 0.81                  | 0.83               | 0.03               |
| 002          | 2.20                  | 8.90                  | 5.55               | 4.74               |

<br>
If the individual sample SD is large, then the concentrations obtained for that sample across reps were discrepant. This could explain why it is an outlier.  
<br>
<br>

**Checking sample processor**  
<br>
Track the team member who processed the sample (centrifuged and aliquoted), then check if patterns emerge between team members.  
<img src="figs/stripplot.png" alt="Calibration Graph" width="400">  
`sns.stripplot(x='Processor', y='Z-score', data=data)`  
<br> 

**Checking the number of freeze/thaw cycles**  
<br>
Each freeze/thaw cycle has a risk of damaging the cell membrane. Damaged cell membranes can affect the stability of measurements, particularly because it can  artifically increase the degree of oxidative stress. >3 cycles could be concerning.  
Check with the team in charge of long-term sample storage for the number of freeze/thaw cycles.  
<br>
<br>

---
**Other notes for MJ**  
Neuro 4-plex (N4PA; GFAP, Tau, UCH-L1, NF-Light): 34 tests, 6-month shelf life  
Cytokine 4-plex (Cyto 4P; IL1-Beta, IL-6, IL-10, TNF-Alpha): 34 tests, 12-month shelf life  
BDNF: 68 tests across 2 plates, 6-month shelf life  


<!--
![calibration graph](figs/calibration_graph.png)
-->
