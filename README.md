# Advanced-Data-Group-Project-3
Data and files for the financialized housing project


# Analysis of FINANCIALIZED HOUSING data set — 2020 to 2021

This repository contains data, analytic code, and findings on the capitalization rates of certain buildings in New York City. This is a key metric for assessing the riskiness of real estate investments. 

## Data

This analysis is based on two spreadsheets.

The spreadsheets come from the following sources:

  - [`acris_sales_2020-2022.csv`](data/acris_sales_2020-2022.csv): Raw data on 2,003 building sales in New York City from the years 2020-2022. These data are based on the BIP Database from the University Neighborhood Housing Program. 
  - [`file_201_data_sm_tract.csv`](file_201_data_sm_tract.csv): Raw data from the Tax Commission Income & Expenses forms, submitted by building owners to the tax commission seeking revisions on their tax payments. This file contains information from 26,887 forms submitted to the tax commission in the year 2021.

These spreadsheets contain, among others, the following columns relevant to the analysis:

- `price_per_bldg` — The sale price of the buildings represented in the acris file.
- `TOTAL INCOME FROM REAL ESTATE` — The annual business income for building owners in the 201 file, including rents, billboards, and ancillary services. 
- `TOTAL EXPENSES` — The total annual expenses for owners represented in the 201 file, such as maintenance and management expenses.
- Borough, Block, and Lot: both files contain information on the BBL of each building, a unique identifier for property plots in New York City. 

## Methodology

The notebook [Cap Rates(final).ipynb](notebooks/Cap Rates(final).ipynb) performs the following analyses:

##### Part 1: Import and Cleaning

- Both spreadsheets were imported into Python and cleaned of duplicates. Both files contained unexpected duplicates--perhaps due to erroneous filings or multiple sales within the two-year period. In order to simplify the analysis, we omitted these data using the drop_duplicates() function. 

##### Part 2: Calculation of Cap Rates

- The two data sets were merged into a single data frame for the 241 unique BBLs that are represented on both data sets. Using the combined dataframe, the columns for income, expenses, and building cost were used to calculate the capitalization ratio for each building, using the formula CR=(I-E)/BC. 
Buildings that do not have enough information to calculate a capitalization rate were dropped using the dropna() function.


##### Part 3: Analysis by Borough


Using these results, we computed the mean and median capitalization rates for each of the four boroughs. Staten Island was not included. 
Our analysis showed: 

  **Brooklyn**: On average borough 3 has the highest capitalization rates (12.6%) all NYC boroughs excluding Staten Island making them the riskiest investments. The low median cap rate (3.8%),however, means the majority of buildings don't possess a high risk for investors. 
  
  **Manhattan**: this borough contains the second highest cap rate (3.44%) on average. Investments here promise lower return but also lower risks for investors. Also the numbers show that most buildings here have an even lower cap rate (2.19%), meaning large inventory of low-profit buildings.
  
  **Bronx**: on average the Bronx has a low cap rate (3.14%). The majority of buildings have a slightly higher cap rate (3.27%). Investors will have an easier time finding similar buildings here. 
  
  **Queens**: this borough has the lowest cap rate (3.08%) and the majority of buildings has a slightly higher cap rate (3.73%). Conditions in Queens are similar to the Bronx. 

  
  
It's worth noting this is only a limited sample and doesn't represent the state of all cap rates in NYC. 

## Outputs

The notebooks output this spreadsheet which contains the merged data from the two spreadsheets, and the capitalization rate for 241 buildings represented on both sheets : [`output/capitalizationrates.csv`](output/capitalizationrates.csv).
Another file, [`output/ResultsByBoro.csv`](output/ResultsbyBoro.csv) contains the mean and median capitalization rates for buildings in this analysis, sorted by borough. Staten Island was not included. 

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- Pandas
- Jupyter Notebooks

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact: 
  - Andrew Ancheta at andrew.ancheta@gmail.com.
  - Nicholas Morgan at nikolaimorgan@protonmail.com.
  - Impu Sehgal at impu.sehgal42@journalism.cuny.edu.
  - Jonnathan Pulla Velecela at j.pullavelecela32@journalism.cuny.edu. 
