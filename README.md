# LTER-pluck

author: Savannah Kjaer

date: 03-18-2026

## Overview

This repository tracks all data processing from the ARC LTER 2024 Pluck.

Quadrats were sampled from the CT, F0.5, F1, F2, F5, and F10 treatments of the MAT06 fertilizer gradient experiment during "peak green" in late July 2024 and sorted within the following days. For "aboveground" (aboveground tissue and rhizomes) samples, four 10 x 40 cm quadrats were removed from each plot (block x treatment) and sorted to species and tissue type. For "belowground" (roots) samples, four 5 x 5 cm quadrats were removed from each plot and sorted by root type. For "total core" samples, four cores were taken from each plot and sorted into aboveground, organic, and mineral horizons. All samples were then dried and weighed.

Samples were then shipped to Lamont. After combining the samples from all four quads within a plot, they were ground and homgenized. A small subsample was run through the elemental analyzer for percent carbon and nitrogen by weight.

Methods can be found here: <https://app.box.com/file/1667812761561>

## Folder organization

-   raw_data - contains unedited, raw copies of all data. DO NOT edit!

-   processed_data - any edited, intermediate versions of data

    -   final_data - final, clean copies of data ready to be published

-   scripts - R Quarto files

-   plots - any plots generated

## Data organization

### scripts/pluck_cleaning.qmd

Read in:

-   /raw_data/**Shoot_data_collection_mass.xlsx**

    -   raw data of aboveground dry masses

-   /raw_data/**Root_data_collection_mass.xlsx**

    -   raw data of belowground dry masses

Wrote:

-   /final_data/**ag_mass.csv**

    -   clean, longform version of aboveground dry masses

-   /final_data/**bg_mass.csv**

    -   clean, longform version of belowground dry masses

-   /final_data/**tc_mass.csv**

    -   clean, longform version of total core dry masses
