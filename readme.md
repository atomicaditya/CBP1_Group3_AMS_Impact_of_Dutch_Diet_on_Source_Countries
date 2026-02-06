# Soy Much at Stake - Dutch Soy Trade & Dietary Land-Use Analysis

Challenge-Based Project analysing the impact of The Netherlands and the Dutch diet on Brazilian soy monoculture. Supervised by University of Amsterdam, in collaboration with Amsterdam Institute for Advanced Metropolitan Solutions. The scientific report and accompanying policy brief supported by this repository are also available here.

The repository consists of **two components**:

-   A global soy trade network and Brazil production risk analysis;
-   A Dutch protein consumption and food-feed land-use model.

All components are described below.

------------------------------------------------------------------------

## Component 1 - Soy Trade Network + Brazil Risk Overlay

This component is looking at how Dutch soy imports connect to global trade
structure and production risks in Brazil.

`Brazil Soy Trade and Climate/Submission_book.ipynb` contains the analysis.

### Contents

#### Global trade (Chatham House)

-   Merge yearly trade spreadsheets;
-   Compute **trade concentration (HHI)** over time;
-   Build **directed trade networks** with `networkx`;
-   Calculate **betweenness centrality** to find key intermediaries;
-   Plot choropleths of:
    -   high centrality countries;
    -   countries with rising centrality (trends).

#### Netherlands-focused research on trade

-   Track NL's **top suppliers** each year;
-   Stability of trade and partner churn;
-   What happens when removing trade nodes.

#### Brazil production side (Trase + MapBiomas + climate)

-   Build a **state-year soy panel** (imports + deforestation);
-   Map:
    -   soy import density (per km²);
    -   soy import exposure (area-normalised).
-   Run a simple **soy vs deforestation regression**;
-   Overlay **gridded climate yield impacts** and aggregate to states;
-   Estimate how yields might change implied imports.

### Outputs

Figures should be saved automatically; otherwise available in the
notebook.

------------------------------------------------------------------------

## Component 2 - Dutch Protein Diets: Food-Feed Competition Model

The second component models how Dutch dietary patterns contribute to soy demand and
associated land use. It integrates consumption data for meat, dairy,
eggs, fish, and plant-based soy substitutes with feed composition,
edible meat conversion ratios, and crop-specific land-use coefficients
to estimate:

-   Soy and total feed land use (m²/person/year);
-   Water footprint per product;
-   Scenario-level impacts of dietary transitions.

Scenarios include a red meat cap, 50/50 and 40/60 animal- and plant
protein targets, and a baseline reflecting current consumption.

`modelling_soy_land_final.ipynb` contains the analysis.

### Inputs / Configurable Parameters

-	Population: `NL_POPULATION`;
-	Protein target: `PROTEIN_TARGET` (kg protein/person/year) – currently at 22kg; can be updated to reflect dietary guidelines;
-	Consumption data: `meat_2024_pc`, `DAIRY_KG_PC`, `EGGS_KG_PC`, `FISH_KG_PC`, `PLANT_MEAT_KG_PC`, `TOFU_KG_PC`, `SOY_MILK_KG_PC` – can be updated with newer consumption data;
-	Scenario settings: Red meat cap (`apply_red_meat_cap` default 10 kg/person/year) and plant-animal protein ratios (50/50 and 40/60) can be modified;
-	Feed composition: `FEED_SHARES` – proportions of crops in animal feed;
-	Land-use coefficients: `CROP_LAND_M2_KG` – area required per kg crop.


### Outputs

Scenario tables and plots covering land use, water footprint, protein
supply, and scenario comparisons.

------------------------------------------------------------------------

## How to run the repository

In a terminal:

1.  Clone the repository

``` bash
git clone https://github.com/atomicaditya/CBP1_Group3_AMS_Impact_of_Dutch_Diet_on_Source_Countries.git
cd CBP1_Group3_AMS_Impact_of_Dutch_Diet_on_Source_Countries
```

2.  Create & activate a virtual environment

``` bash
python -m venv venv
```

Activate:

Windows:

```bash
venv\Scripts\activate
```

Mac/Linux:
```bash
source venv/bin/activate
```

3.  Install dependencies

``` bash
pip install -r requirements.txt
```

4.  Run each notebook in sequence. Make sure the newly created virtual environment is selected as the kernel.

------------------------------------------------------------------------

## Notes

### Component 1

- Very “research notebook” style (not packaged/cleaned);
- A few sections marked experimental;
- Climate → import effects are simple approximations, not a full model.

### Component 2

-	Protein intake is expressed for unprocessed products; processed foods are not included;
-	Feed land excludes pasture, grassland, housing, and on-farm infrastructure;
-	Scenario logic scales protein sources to meet dietary targets; plant-based substitutions can be modified in plant_shares.

