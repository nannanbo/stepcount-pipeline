# Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts
 
This repository contains the R code supporting:
 
> Nannan Bo, MB; Alyssa M. Sudnick, MS; Julie D. Counts, RD, MS; Katie G. Kennedy, MS; Agustin A. Saldana, MS; Katherine A. Collins-Bennett, PhD; William C. Bennett, MS; Johanna L. Johnson, MS; Kim M. Huffman, MD, PhD; Amanda E. Paluch, PhD; Marissa C. Ashner, PhD; William E. Kraus, MD; Sarah B. Peskoe, PhD*; Leanna M. Ross, PhD *A Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts: Application and Evaluation in the STRRIDE-PD Reunion Study.*
 
---
 
## Overview
 
This pipeline transforms epoch-level step-count data from commercial Garmin wearable devices into participant-level analytic variables suitable for epidemiologic research. It was developed for and applied to the STRRIDE-PD Reunion study, a long-term follow-up cohort of older adults originally enrolled in a supervised exercise intervention trial.
 
The pipeline makes all analytic decisions explicit and reproducible, including timestamp standardization, daily epoch grid reconstruction, wear-time inference from observed step patterns, valid-day classification, and participant-level summary generation. They are declared in a single configuration block at the top of the document and propagated throughout, so that any parameter change requires editing only one location.
 
---

## Repository Contents
 
| File | Description |
|---|---|
| `step_count_pipeline.Rmd` | Fully documented R Markdown pipeline (source) |
| `step_count_pipeline.html` | Knitted HTML |
| `README.md` | This file |
 
The `.Rmd` file is the primary deliverable. The knitted `.html` provides a readable view of the pipeline without requiring R to be installed.

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
 
All parameters below are defined in the `config` chunk at the top of `step_count_pipeline.Rmd` and can be modified without changing any downstream code.
 
| Parameter | Value used | Justification |
|---|---|---|
| Epoch length | 15 minutes | Device default (Garmin vívosmart 5 via Pattern Health) |
| Max gap treated as non-wear | 100 consecutive epochs | Runs of ≥ 100 missing epochs excluded from zero-imputation |
| Wear-time inference | First to last non-zero step epoch within each day | No device-generated wear indicators available |
| Valid-day threshold (primary) | ≥ 10 hours inferred wear time | Consistent with NHANES conventions and accelerometer literature |
| Valid-day threshold (sensitivity) | ≥ 6 hours inferred wear time | Evaluated in sensitivity analysis |
| Minimum valid days per participant | ≥ 4 days | Consistent with evidence for reliable habitual PA estimation in older adults |
 
---
 
## Citation
 
If you use this pipeline in your work, please cite:
 
> Nannan Bo, MB; Alyssa M. Sudnick, MS; Julie D. Counts, RD, MS; Katie G. Kennedy, MS; Agustin A. Saldana, MS; Katherine A. Collins-Bennett, PhD; William C. Bennett, MS; Johanna L. Johnson, MS; Kim M. Huffman, MD, PhD; Amanda E. Paluch, PhD; Marissa C. Ashner, PhD; William E. Kraus, MD; Sarah B. Peskoe, PhD*; Leanna M. Ross, PhD *A Reproducible Pipeline for Processing Commercial Wearable Step-Count Data in Aging Cohorts: Application and Evaluation in the STRRIDE-PD Reunion Study.*
 
---
 
## Contact
 
Nannan Rena Bo  
rena.bo@duke.edu
Duke University 

## ACKNOWLEDGEMENTS

We would like to thank all of the STRRIDE-PD Reunion participants, staff members, and student interns.

## SOURCES OF FUNDING

This publication was made possible in part by the following grants from the National Institutes of Health: R21AG075379 from the National Institute on Aging (NIA); P30AG028716 (Duke Claude D. Pepper Older Americans Independence Center) from the NIA; UL1TR002553 from the National Center for Advancing Translational Sciences; and K01HL177266 (KACB) from the National Heart, Lung, and Blood Institute. LMR was additionally supported by Career Development Awards from the American Heart Association (23CDA1051777) and the Duke Pepper Older Americans Independence Center's Research Education Component (5P30AG028716-18).

## DISCLOSURES

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper. 

## DATA AVAILABILITY

The raw data supporting the conclusions of this article will be made available by the authors without undue reservation. Requests to access the data should be directed to WEK.

