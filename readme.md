# Soy trade network + Brazil risk overlay

CBP Project looking at how Dutch soy imports connect to  global trade structure and production risks in Brazil.

Submission_book.ipynb contains the main analysis

## Contents

### Global trade (Chatham House)
- Merge yearly trade spreadsheets  
- Compute **trade concentration (HHI)** over time  
- Build **directed trade networks** with `networkx`  
- Calculate **betweenness centrality** to find key intermediaries  
- Plot choropleths of:
  - high centrality countries  
  - countries with rising centrality (trends)

### Netherlands-focussed research on trade
- Track NL’s **top suppliers** each year  
- Stability of trade and partner churn
- What happens when removing trade nodes

### Brazil production side (Trase + MapBiomas + climate)
- Build a **state–year soy panel** (imports + deforestation)  
- Map:
  - soy import density (per km²)  
  - soy import exposure (area-normalised)  
- Run a simple **soy vs deforestation regression**  
- Overlay **gridded climate yield impacts** and aggregate to states  
- Estimate how yields might change implied imports

## Outputs
Figures should be saved automatically; otherwise available in the notebook.

## How to run
1. Install: `pandas numpy matplotlib networkx plotly scipy openpyxl requests`
2. run the notebook in sequence

## Notes
- Very “research notebook” style (not packaged/cleaned)
- A few sections marked experimental
- Climate → import effects are simple approximations, not a full model
