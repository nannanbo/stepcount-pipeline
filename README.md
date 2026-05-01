# Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts
 
This repository contains the R code supporting:
 
> Nannan Bo, Leanna M. Ross, PhD, Sarah B. Peskoe, PhD, Alyssa M. Sudnick, MS, Julie D. Counts, MS, Agustin A. Saldana, MS, Kathryn G. Kennedy, MS, Katherine A. Collins-Bennett, PhD, Kim M. Huffman, MD, PhD, Amanda E. Paluch, PhD Marissa C. Ashner, PhD, William E. Kraus, MD *A Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts: Application and Evaluation in the STRRIDE-PD Reunion Study.*
 
---
 
## Overview
 
This pipeline transforms epoch-level step-count data from commercial Garmin wearable devices into participant-level analytic variables suitable for epidemiologic research. It was developed for and applied to the STRRIDE-PD Reunion study, a long-term follow-up cohort of older adults originally enrolled in a supervised exercise intervention trial.
 
The pipeline makes all analytic decisions explicit and reproducible, including timestamp standardization, daily epoch grid reconstruction, wear-time inference from observed step patterns, valid-day classification, and participant-level summary generation.
 
---

## Data Availability
 
The STRRIDE-PD Reunion study data are not publicly available due to participant privacy protections and IRB restrictions.
 
The code is structured to run on epoch-level step-count data exported from Garmin devices via the Pattern Health platform, formatted as timestamped values aggregated in 15-minute intervals.
 
---
 
## Requirements
 
- **R** (developed and tested on R version 4.5.1)
- Required packages:
```r
install.packages(c(
  "dplyr",
  "tidyr"
  "ggplot2"
))
```
 
---
 
## Key Analytic Decisions
 
| Decision | Value used | Justification |
|---|---|---|
| Epoch length | 15 minutes | Device default (Garmin vívosmart 5 via Pattern Health) |
| Wear-time inference | First to last non-zero step epoch within each day | No device-generated wear indicators available |
| Valid-day threshold (primary) | ≥ 10 hours inferred wear time | Consistent with NHANES conventions and accelerometer literature |
| Valid-day threshold (sensitivity) | ≥ 6 hours inferred wear time | Evaluated in sensitivity analysis; results identical |
| Minimum valid days per participant | ≥ 4 days | Consistent with evidence for reliable habitual PA estimation in older adults |
 
---
 
## Citation
 
If you use this pipeline in your work, please cite:
 
> Nannan Bo, Leanna M. Ross, PhD, Sarah B. Peskoe, PhD, Alyssa M. Sudnick, MS, Julie D. Counts, MS, Agustin A. Saldana, MS, Kathryn G. Kennedy, MS, Katherine A. Collins-Bennett, PhD, Kim M. Huffman, MD, PhD, Amanda E. Paluch, PhD Marissa C. Ashner, PhD, William E. Kraus, MD *A Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts: Application and Evaluation in the STRRIDE-PD Reunion Study.*
 
---
 
## Contact
 
Nannan Rena Bo  
rena.bo@duke.edu
Duke University 

