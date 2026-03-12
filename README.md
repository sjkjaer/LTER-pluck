# LTER-pluck

Data from the LTER 2024 pluck

## Folder organization

-   raw_data - contains unedited, raw copies of all data. DO NOT edit!

-   processed_data - any and all edited versions of data

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

-   /processed_data/final_data/**ag_mass_quad.csv**

    -   clean, longform version of aboveground dry masses

-   /processed_data/**ag_ids.csv**

    -   one ID value for each plot, the first occurence of the ID value from each quad, for use with the EA data
    
-   /processed_data/**ag_id_mass.csv**

    -   one ID value per plot and the sum mass across all 4 quads of that plot
    -   may remove the Total_mass_g bc it's a repeat of quads
    
-   /processed_data/**bg_ids.csv**

    -   one ID value for each plot, the first occurence of the ID value from each quad, for use with the EA data
    
-   /processed_data/final_data/**bg_mass_quad.csv**

    -   clean, longform version of belowground dry masses
    
-   /processed_data/**bg_id_mass.csv**

    -   one ID value per plot and the sum mass across all 4 quads of that plot
    -   may remove the Total_mass_g bc it's a repeat of quads   
