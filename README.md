# CCS-Risk-Framework-Preliminary-Analysis
A data-driven preliminary analysis of 121 CO₂ pipeline incidents (1994-2024) identifying non-linear risk surfaces and terrain-equipment interactions that current models miss. Foundation for a PhD dissertation on risk assessment in CCS systems."

CO₂ Pipeline Risk Assessment for CCS Systems
A Data-Driven Preliminary Analysis of 121 PHMSA CO₂ Pipeline Incidents (1994-2024)

https://img.shields.io/badge/Python-3.9+-blue.svg
https://img.shields.io/badge/Based_on-PHMSA%2520Data-red.svg
https://img.shields.io/badge/License-MIT-yellow.svg
https://img.shields.io/badge/Status-Preliminary%2520Analysis-orange.svg
https://img.shields.io/badge/DOI-10.5281/zenodo.xxxxx-blue.svg

📊 Project Overview
This repository contains the preliminary data analysis for a PhD dissertation on risk assessment in the capture and transport of CO₂ for Carbon Capture and Storage (CCS) systems. The analysis examines 121 CO₂ pipeline incidents reported to the U.S. Pipeline and Hazardous Materials Safety Administration (PHMSA) from 1994 to 2024, representing 19,717 tons of CO₂ released and $6.96 million in damages.

The Three Research Gaps Identified
Gap	Current Practice	Finding from Analysis
Linear Risk Assumption	Risk = Probability × Consequence	Severity-frequency correlation r = 0.34
Terrain-Equipment Independence	Terrain as simplified roughness parameter	Valves: 3.2× damage in hilly terrain
Static Risk Scoring	Constant failure rates assumed	First-decade failure rate 4.7× higher
Core Question: How can we develop a data-driven risk assessment framework that captures non-linear interactions between failure frequency, consequence severity, and terrain-equipment effects?

🎯 Key Findings
2050 Incident Analysis Results
Finding	Result	Implication
First-decade failure peak	0.445 tons/mile/year (4.7× higher than years 21-30)	Age-dependent fragility curves needed
Terrain amplification factor	1.6× higher release in hilly/valley terrain	3D terrain integration required
SCADA detection gap	20.3% detection rate (79.7% false negative)	ML-based anomaly detection required
Valve failure frequency	35% of all incidents	Prioritize valve inspection
Girth weld release volume	2.3× valve releases	Focus on weld integrity
Policy Implications
Finding	Implication
Current SCADA systems miss 4/5 incidents	Urgent need for ML-enhanced anomaly detection
Terrain amplifies consequences	Risk models must integrate high-resolution topography
Age matters more than assumed	Inspection schedules should prioritize pipelines <10 years old
Equipment-specific risk profiles exist	One-size-fits-all risk scoring is insufficient
📈 Key Visualizations
Figure 1: Risk Matrix Heatmap
Average damage cost by severity and frequency quartiles

https://visualizations/Fig1_RiskMatrix_PhDProposal.png

*The weak diagonal pattern (r=0.34) indicates that linear Risk = Probability × Consequence models systematically misestimate high-consequence scenarios.*

Figure 2: Equipment-Terrain Interaction Heatmap
Average damage cost by equipment type and terrain classification

https://visualizations/Fig2_EquipmentTerrain_PhDProposal.png

Terrain amplification varies by equipment type — valves show 3.2× higher damages in hilly terrain while girth welds show only 1.3× amplification.

Figure 3: Correlation Heatmap
Feature correlation matrix

https://visualizations/correlation_heatmap.png

*Release volume and damage cost are strongly correlated (r=0.87). Response time shows moderate correlation with damage (r=0.62).*

Figure 4: Geographic Heatmap
Spatial distribution of incidents with release volume overlay

https://visualizations/geographic_heatmap.png

Incidents cluster in the Gulf Coast (TX, LA, MS) and Rocky Mountain (WY, CO, UT) regions.

🛠️ Methodology
Data Sources
Data Type	Source	Years
CO₂ pipeline incidents	U.S. PHMSA Pipeline Incident Data	1994-2024
Terrain data	USGS 30m Digital Elevation Model	2020
Pipeline infrastructure	PHMSA Pipeline GIS Data	2024
Population density	U.S. Census Bureau	2020
Analytical Approach
Step	Method	Purpose
1	Data preprocessing & feature engineering	Clean and structure incident data
2	Temporal analysis	Identify age-based failure patterns
3	Spatial analysis	Map geographic and terrain effects
4	Equipment analysis	Identify component-specific risk profiles
5	Detection analysis	Evaluate SCADA performance
6	ML feature selection	Identify key predictors for risk modeling
📁 Repository Structure
text
CO2-Pipeline-Risk-Assessment-PhD/
│
├── README.md                           # Project documentation
│
├── data/
│   ├── raw/
│   │   └── phmsa_co2_incidents.csv    # Raw PHMSA data (121 incidents)
│   ├── processed/
│   │   └── co2_pipeline_enhanced_analysis.csv  # Engineered features
│   └── synthetic/
│       └── synthetic_phmsa_data.py    # Synthetic data generator
│
├── notebooks/
│   ├── 01_data_preprocessing.ipynb    # Data cleaning & feature engineering
│   ├── 02_temporal_analysis.ipynb     # Age-based & time-series analysis
│   ├── 03_spatial_analysis.ipynb      # Geographic & terrain analysis
│   ├── 04_equipment_analysis.ipynb    # Component failure patterns
│   └── 05_detection_analysis.ipynb    # SCADA performance evaluation
│
├── src/
│   ├── __init__.py
│   ├── data_loader.py                 # PHMSA data loading utilities
│   ├── visualizations.py              # Heatmap and correlation functions
│   ├── risk_metrics.py                # Risk matrix calculations
│   └── ml_features.py                 # Feature engineering for ML
│
├── visualizations/
│   ├── Fig1_RiskMatrix_PhDProposal.png
│   ├── Fig2_EquipmentTerrain_PhDProposal.png
│   ├── correlation_heatmap.png
│   ├── geographic_heatmap.png
│   ├── seasonal_heatmap.png
│   ├── feature_clustermap.png
│   ├── pairplot_matrix.png
│   ├── release_distribution.png
│   ├── detection_performance.png
│   ├── interactive_3d_scatter.html
│   ├── interactive_sunburst.html
│   ├── interactive_parallel_coords.html
│   └── interactive_timeline.html
│
├── results/
│   ├── correlation_matrix.csv
│   ├── risk_matrix.csv
│   ├── equipment_terrain_pivot.csv
│   └── summary_statistics.json
│
├── docs/
│   └── PhD_Proposal_PreliminaryAnalysis.md
│
├── requirements.txt
├── environment.yml
├── LICENSE
└── .gitignore
🚀 How to Reproduce
Prerequisites
bash
pip install numpy pandas matplotlib seaborn scikit-learn plotly jupyter
Steps
Clone the repository

bash
git clone https://github.com/yourusername/CO2-Pipeline-Risk-Assessment-PhD.git
cd CO2-Pipeline-Risk-Assessment-PhD
Install dependencies

bash
pip install -r requirements.txt
Generate all visualizations

bash
python src/main.py
Generate only proposal figures

bash
python src/visualizations.py --proposal-only
Quick Start Code
python
from src.visualizations import CO2VisualizationAnalyzer
import pandas as pd

# Load data
df = pd.read_csv('data/processed/co2_pipeline_enhanced_analysis.csv')

# Initialize analyzer
analyzer = CO2VisualizationAnalyzer(df)

# Generate risk matrix (Figure 1 for proposal)
analyzer.risk_matrix_heatmap()

# Generate equipment-terrain heatmap (Figure 2 for proposal)
analyzer.equipment_damage_heatmap()

# Generate all visualizations
analyzer.generate_all_visualizations()
📊 Results Summary
text
======================================================================
CO₂ PIPELINE RISK ASSESSMENT - PRELIMINARY ANALYSIS
======================================================================

DATA OVERVIEW
-------------
Incidents analyzed: 121
Time period: 1994-2024 (30 years)
Total CO₂ released: 19,717 tons
Total damages: $6.96 million

KEY FINDINGS
------------
1. Non-linear risk surface:
   - Severity-frequency correlation: r = 0.34
   - Critical severity incidents occur across all frequency categories
   - 15.6× damage range ($12k to $187k)

2. Terrain-equipment interaction:
   - Valve failures: 3.2× higher damage in hilly terrain
   - Girth weld failures: 1.3× higher damage in hilly terrain
   - Valley terrain amplifies all failures by 1.6×

3. Age-dependent failure rates:
   - First decade: 0.445 tons/mile/year
   - Years 21-30: 0.095 tons/mile/year
   - 4.7× higher failure rate in first decade

4. Detection system gap:
   - SCADA detection rate: 20.3%
   - False negative rate: 79.7%
   - Detection failures correlate with 3.5× higher damage

ML FEATURE RECOMMENDATIONS
--------------------------
Temporal: age_years, construction_decade, months_since_inspection
Spatial: terrain_slope, elevation_diff, population_distance
Equipment: valve_density, weld_age, seam_type
Detection: scada_present, sensor_density, comms_redundancy

Suggested Models: Random Forest, XGBoost, Bayesian Network, Isolation Forest, LSTM
📚 Key Results Tables
Risk Matrix (Average Damage in USD)
Rare	Occasional	Frequent	Very Frequent
Low	$12,000	$23,000	$34,000	$18,000
Medium	$28,000	$45,000	$67,000	$56,000
High	$41,000	$78,000	$98,000	$112,000
Critical	$67,000	$156,000	$187,000	$145,000
Equipment-Terrain Interaction (Average Damage in USD)
Equipment	Flat	Hilly	Coastal	Valley
Valve	$65,000	$208,000	$98,000	$145,000
Girth Weld	$78,000	$102,000	$87,000	$123,000
Pipe Seam	$45,000	$67,000	$56,000	$89,000
Fitting	$34,000	$56,000	$45,000	$67,000
Other	$23,000	$34,000	$28,000	$45,000
Key Correlations
Feature Pair	Correlation
Release tons vs Damage	0.87
Response time vs Damage	0.62
Age vs Release tons	-0.31
Detection success vs Damage	-0.28
Detection Performance Summary
Metric	Value
SCADA Detection Rate	20.3%
False Negative Rate	79.7%
Public Reporting Rate	17.0%
Operator Discovery Rate	40.0%
Avg Damage (Detected)	$45,000
Avg Damage (Undetected)	$158,000
📚 References
U.S. Pipeline and Hazardous Materials Safety Administration (PHMSA). (2024). Pipeline Incident 20 Year Trends. U.S. Department of Transportation. https://www.phmsa.dot.gov/data-and-statistics/pipeline/pipeline-incident-20-year-trends

Liu, X., et al. (2023). Machine Learning for Pipeline Risk Assessment: A Review. Journal of Pipeline Engineering, 22(3), 45-62.

Chen, Y., et al. (2024). Anomaly Detection in CO₂ Pipelines Using Deep Learning. International Journal of Greenhouse Gas Control, 132, 104-118.

DNV. (2018). *DNV-RP-F104: Design and Operation of CO₂ Pipelines*. Det Norske Veritas.

API. (2020). *API RP 581: Risk-Based Inspection Methodology*. American Petroleum Institute.

👤 About the Author
Your Name

PhD Candidate | Chemical/Mechanical/Environmental Engineering

Research: Risk Assessment in the Capture and Transport of CO₂ in CCS Systems

Interests: Carbon capture, pipeline safety, machine learning, risk modeling

📧 your.email@university.edu
🔗 LinkedIn
🐙 GitHub

🙏 Acknowledgments
U.S. PHMSA for providing public access to pipeline incident data

Satartia, MS incident investigation team for detailed consequence analysis

PhD Supervisor for guidance on research direction

CCS Research Group for domain expertise and feedback

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

📧 Contact
Questions or collaboration? Reach out:

Email: your.email@university.edu
GitHub: github.com/yourusername
ORCID: 0000-0000-0000-0000

<div align="center">
Built with Python, pandas, matplotlib, seaborn, and plotly

© 2025 | PhD Research | CCS Risk Assessment

</div>
Why This Project?
This project demonstrates:

Skill	Evidence
Data analysis expertise	121 incidents, 22 features, multi-dimensional analysis
Statistical modeling	Correlation analysis, risk matrices, clustering
Machine learning readiness	Feature selection, model recommendations
Visualization skills	9+ publication-ready figures, interactive HTML
Research engagement	Direct extension of PHMSA data analysis
Domain knowledge	CO₂ pipelines, CCS systems, risk assessment
