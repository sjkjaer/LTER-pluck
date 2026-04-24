# LTER-pluck

author: Savannah Kjaer

date: 03-18-2026

## Overview

This repository tracks all data processing from the ARC LTER 2024 Pluck.

Quadrats were sampled from the CT, F0.5, F1, F2, F5, and F10 treatments of the MAT06 fertilizer gradient experiment during "peak green" in late July 2024 and sorted within the following days. For "aboveground" (aboveground tissue and rhizomes) samples, four 10 x 40 cm quadrats were removed from each plot (block x treatment) and sorted to species and tissue type. For "belowground" (roots) samples, four 5 x 5 cm quadrats were removed from each plot and sorted by root type. For "total core" samples, four cores were taken from each plot and sorted into aboveground, organic, and mineral horizons. All samples were then dried and weighed.

Samples were then shipped to Lamont. After combining the samples from all four quads within a plot, they were ground and homgenized. A small subsample was run through the elemental analyzer for percent carbon and nitrogen by weight.

Methods can be found here: <https://app.box.com/file/1667812761561>

It also includes cleaning 2012 pluck data to make it easier to use in R and ready to publish to EDI.

## Folder organization

-   2012_pluck - everything related to 2012 pluck data cleaning
  
    -   raw_data - contains unedited, raw copies of all data. DO NOT edit!

    -   processed_data - any edited, intermediate versions of data

        -   final_data - final, clean copies of data ready to be published

    -   scripts - R Quarto files

    -   plots - any plots generated

-   2024_pluck - everything related to 2024 pluck data cleaning

    -   same organization as above

## Data organization

### 2024_pluck/scripts/pluck_cleaning.qmd

Notes:

-   Dropped columns and notes that only pertained to pluck organization (sample weigher, etc)
-   Created a longform mass table
-   Created a 'plot_tissue_id' which is the first appearance of a bag number across quads, within a plot, species, and tissue type. This was the ID used when quads were combined to run on the EA.
-   Standardized column names to snake case
-   Added relevant notes
-   Removed plot_tissue_id's that I had added to distinguish burnt B1 CT Q3&4 samples from unburnt Q1&2, but decided to exclude the burnt samples anyway (see below, AG).
-   Expanded six letter species codes into full names (AG)
-   Added a 'growth_form' column (AG)
-   If a core was redone for "sludge", removed the first core and kept the redo sample, noted. (TC)

Read in:

-   ../raw_data/**Shoot_data_collection_mass.xlsx**

    -   raw data of aboveground dry masses

-   ../raw_data/**Root_data_collection_mass.xlsx**

    -   raw data of belowground dry masses

Wrote:

-   ../processed_data/final_data/**ag_mass.csv**

    -   clean, longform version of aboveground dry masses

-   ../processed_data/**ag_pluck_id.csv**

    -   list of id numbers for species, tissue type in each plot

-   ../final_data/**bg_mass.csv**

    -   clean, longform version of belowground dry masses

-   ../processed_data/**bg_pluck_id.csv**

    -   list of id numbers for horizon, root type in each plot

-   ../final_data/**tc_mass.csv**

    -   clean, longform version of total core dry masses


### 2024_pluck/scripts/EA_cleaning.qmd

Notes:

- Each individual EA run was combined into one spreadsheet, CN_results2.xlsx
- Dropped unhelpful columns from the EA output
- Corrected ID numbers by referencing photos of the handwritten mass datasheets
- Combine CN results with IDs to get block, treatment, species, tissue, etc
- Left out single quads that were missed in combining with the others in a plot, then redone alone, so as to not over-represent them.
- Standardized column names to snake case
- Removed burnt samples. These samples were exposed to too high drying oven temps and were visibly blackened. I compared the burnt block to unburnt blocks, but with such a small sample size didn't feel like I could say they weren't affected, so chose to just remove them (AG).
- Renamed to plot_root_id (BG) and plot_horizon_id (TC)
- Corrected T to M for mineral (TC)
- separated plot_horizon_id into block, treatment, horizon columns (TC), no id numbers used

Read in:

-   ../raw_data/**CN_results2.xlsx**

-   ../processed_data/**ag_pluck_id.csv**

-   ../processed_data/**bg_pluck_id.csv**

Wrote:

-   ../final_data/**ag_cn.csv**

    -   CN results for each plot, species, tissue type combined across quads for AG samples

-   ../final_data/**bg_cn.csv**

    -   CN results for each plot, horizon, root type combined across quads for BG samples

-   ../final_data/**tc_cn.csv**

    -   CN results for each plot and horizon combined across quads for total core samples


### 2012_pluck/scripts/2012_pluck_cleaning.qmd

Notes:

- Removed any calculations from data, just kept raw data
- Created a longform table
- Separated the 'block_quad' column into two separate columns
- changed the site name from LTER 2006 Low Nutrient Moist Acidic Tussock Tundra to MAT06 to match current site naming conventions
- Standardized column names to snake case

Read in:

-   ../raw_data/**2012lg06ttbiomass Sep23.xlsx**

    -   raw data of dry masses

Wrote:

-   ../processed_data/final_data/**mass_2012.csv**

    -   clean, longform version of dry masses
