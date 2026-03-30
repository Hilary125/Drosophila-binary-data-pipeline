Analysis code for a multi-student Drosophila microfluidic chip experiment examining how genotype and chip geometry affect larval development outcomes.

Overview
Larval outcome data were collected by ~30 student groups across several weeks. Each record corresponds to one fly channel containing one larva/pupa. The analysis examines transfer rate, hatch rate, wing defect rate, and sex ratio across genotypes and chip types, with controls for operator variability and collection date.

Repository Contents
drosophila_analysis_final.ipynb   # Full analysis pipeline (see sections below)
README.md
requirements.txt

Note: Raw data are not included in this repository as the dataset is unpublished. Data are available from the corresponding author upon reasonable request.


Analysis Pipeline
The notebook is organised into the following sections:
SectionDescription1–3Setup, data loading, column renaming4Quality control and pre-specified exclusion criteria5Dataset overview and summary counts6Date effect on hatch rate (two-way ANOVA, interaction plots)7Transfer rate by genotype (operator skill proxy)8Hatch rate by genotype and chip type; student-level exclusions9Sex ratio of hatched adults10Wing defect rate (primary outcome); eye and leg defects for context11Statistical testing: Fisher's exact, Mann-Whitney U, odds ratios, absolute risk differences, p-value heatmap12Inter-operator variability analysis (SD, CV by genotype)13Survivorship bias analysis14Multiple testing correction (Benjamini-Hochberg FDR)15Mixed-effects logistic regression (GLMM) with student as random effect16Genotype × chip type interaction (two-way ANOVA + GLMM); chip main effects; within-genotype chip comparisons17Transfer rate as a potential confoundResults SummaryAuto-generated summary of all key statisticsSave OutputsExports cleaned data and figures

Data Structure
Each record contains the following variables:
ColumnDescriptiondateExperiment date (YYYYMMDD)fly_idUnique fly code encoding student, genotype, and chipgenotypeExperimental genotype (harmonised)chip_typeOne of three chip designs (straight, 0.3 double, 0.3 multi)transferredWhether larva/pupa was successfully loaded (Y/N)hatchedWhether adult eclosed (Y/N)sexAdult sex (M/F)defect_eyeEye morphological defect (Y/N)defect_legLeg morphological defect (Y/N)defect_wingWing morphological defect (Y/N) — primary outcomestudent_idAnonymised operator identifier

Requirements
All analyses were performed in Python 3.12.7. Install dependencies with:
bashpip install -r requirements.txt
Core packages: pandas, numpy, matplotlib, seaborn, scipy, statsmodels

Usage

Place your data files (.xlsx format, one per student group) in a folder and update the DATA_FOLDER variable at the top of the notebook.
Run cells sequentially from top to bottom.
Outputs (figures and summary tables) are saved to the path specified in TAB_FOLDER.

