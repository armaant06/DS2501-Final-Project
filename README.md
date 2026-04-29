# DS2501-Final-Project

NYC Motor Vehicle Collision Analysis
Overview
This project analyzes police-reported motor vehicle collisions in New York City from 2017–2022 to identify variables associated with collision occurrence and severity. The goal is to surface data-driven insights that can inform public safety policy in NYC and other major cities.
The analysis covers:

Casualty breakdown by pedestrians, cyclists, and motorists (injuries and fatalities)
Collision patterns by time of day and season
Geographic concentration by borough and intersection
Most common vehicle types involved in crashes
Top contributing factors to collisions


Project Structure
textnyc-collisions/
│
├── FinalProject.ipynb
├── final_code.py
├── collisions.csv
└── README.md

Running the Project
1. Clone or Download the Project
Place all project files in the same folder, including collisions.csv.
2. Create and Activate a Python Environment
bashpython -m venv env
Windows
bashenv\Scripts\activate
Mac/Linux
bashsource env/bin/activate
3. Install Required Packages
bashpip install pandas numpy scipy matplotlib
4. Run the Analysis
bashpython final_code.py
Or open and run FinalProject.ipynb in Jupyter or Google Colab.

Usage
Time of Day & Season

Crash counts grouped into morning, afternoon, evening, and night
Crash counts grouped by season (spring, summer, fall, winter)

Location Analysis

Bar chart of collision counts by NYC borough
Top 5 highest-crash intersections printed to console

Vehicle Type Analysis

Bar chart of the five most common vehicle types involved in crashes
Vehicle type labels are normalized and deduplicated across all five vehicle columns

Contributing Factors

Top 5 most frequent contributing factors printed to console
Excludes vague labels such as "Unspecified" and "Other Vehicular"

Casualty Analysis

Descriptive statistics (mean, median, mode, std, min, max, range, total) for pedestrian, cyclist, and motorist injuries and fatalities
2×2 bar chart grid comparing mean and total injuries and fatalities across groups


Architecture
Data Layer
load_data() — loads collisions.csv from Google Drive (Colab) or local environment with automatic fallback.
clean_data() — drops columns with no analytical value: LATITUDE, LONGITUDE, LOCATION, ZIP CODE, and COLLISION_ID. Missing values are handled feature-by-feature during analysis rather than dropped upfront, preserving sample size.
Analysis & Visualization Functions
FunctionAuthorPurposetime_of_day()ArmaanCategorizes crashes by hour into morning / afternoon / evening / nighttime_of_year()ArmaanCategorizes crashes by month into seasonsborough(), borough_vis()ChelseaCounts and plots crashes by boroughintersection()ChelseaIdentifies top crash intersectionsvehicle_type(), vehicle_type_vis()ChelseaAggregates and plots vehicle types across 5 columnscont_facts()AnamikaFilters and ranks contributing factors by frequencydescriptives(), print_stats()AnamikaComputes and prints descriptive statistics for any columntype_casualty_vis()AnamikaPlots injury and fatality counts by group

Data Quality Notes

The dataset covers only police-reported collisions, meaning minor incidents with no injury and under $1,000 in damage may be underrepresented.
Most variables are categorical, which prevented use of ANOVA and linear regression. A severity scoring matrix was created as a workaround to enable some comparison across collision types.
Borough and intersection counts are influenced by population density and traffic volume rather than inherent risk alone.


Dependencies

pandas / NumPy / SciPy / Matplotlib


Dataset
Motor Vehicle Collisions – Crashes, City of New York via data.gov. 29 columns, 2M+ rows, 2017–2022.

Authors
Anamika Pusalkar, Chelsea Kwan, and Armaan Thomas — DS 2500, Northeastern University (December 2025)
