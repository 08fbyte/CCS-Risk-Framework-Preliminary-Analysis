# CCS-Risk-Framework-Preliminary-Analysis
A data-driven preliminary analysis of 121 CO₂ pipeline incidents (1994-2024) identifying non-linear risk surfaces and terrain-equipment interactions that current models miss. Foundation for a PhD dissertation on risk assessment in CCS systems."
📋 Overview
This repository contains the preliminary data analysis for a PhD dissertation on risk assessment in the capture and transport of CO₂ for Carbon Capture and Storage (CCS) systems.

Metric	Value
Incidents Analyzed	121
CO₂ Released	19,717 tons
Total Damages	$6.96 million
Time Period	1994–2024 (30 years)
🔍 Key Findings
Finding	Result	Implication
Non-linear risk surface	Severity-frequency correlation r = 0.34	Linear Risk = P × C models insufficient
Terrain-equipment interaction	Valves: 3.2× damage in hilly terrain	Terrain effects are equipment-dependent
First-decade failure peak	0.445 tons/mile/year (4.7× higher)	Age-dependent fragility curves needed
SCADA detection gap	20.3% detection rate (79.7% false negative)	ML-based anomaly detection required
Research Gap Identified: Current frameworks (API RP 581, DNV-RP-F104, EFFECTS, PHAST, SLAB) assume linear risk surfaces, constant failure rates, and independent feature effects. This analysis demonstrates all three assumptions are violated for CO₂ pipelines.

📊 Complete Visualization Gallery
🎯 Primary Figures (for PhD Proposal)
Figure 1: Risk Matrix Heatmap
Average damage cost by severity and frequency quartiles

[Insert Fig1_RiskMatrix_PhDProposal.png]

Key Insight: Severity and frequency are weakly correlated (r=0.34), demonstrating non-linear risk surfaces that current linear models cannot capture.

Figure 2: Equipment-Terrain Interaction Heatmap
Average damage cost by equipment type and terrain classification

[Insert Fig2_EquipmentTerrain_PhDProposal.png]

Key Insight: Terrain amplification is equipment-dependent — valves show 3.2× higher damages in hilly terrain while girth welds show only 1.3× amplification.

📈 Exploratory Analysis Figures
Figure 3: Correlation Heatmap
Pearson correlation matrix of all numeric features

[Insert correlation_heatmap.png]

Key Insight: Release volume and damage cost are strongly correlated (r=0.87). Response time shows moderate correlation with damage (r=0.62), justifying faster detection systems.

Figure 4: Geographic Heatmap
Spatial distribution of incidents with release volume overlay

[Insert geographic_heatmap.png]

Key Insight: Incidents cluster in the Gulf Coast (TX, LA, MS) and Rocky Mountain (WY, CO, UT) regions. Bubble size represents release volume.

Figure 5: Seasonal Heatmap
Temporal patterns by hour of day and month

[Insert seasonal_heatmap.png]

Key Insight: Incidents show seasonal variation with higher frequency during Summer months, potentially related to temperature effects on pipeline materials.

Figure 6: Feature Clustermap
Hierarchical clustering of incidents by key features

[Insert feature_clustermap.png]

Key Insight: Incidents naturally cluster into distinct groups based on feature similarity, suggesting multiple failure modes exist.

Figure 7: Pairplot Matrix
Multi-dimensional feature relationships by terrain type

[Insert pairplot_matrix.png]

Key Insight: Terrain type separates incident characteristics, with hilly terrain showing higher release volumes across all features.

Figure 8: Release Volume Distribution
Distribution and comparison by equipment and terrain

[Insert release_distribution.png]

Key Insight: Release volumes follow a log-normal distribution. Girth welds show the widest range of release volumes.

Figure 9: Detection Performance Plot
SCADA detection rate and damage correlation

[Insert detection_performance.png]

Key Insight: Detection failures correlate with 3.5× higher average damages, highlighting the need for improved monitoring systems.

🌐 Interactive Visualizations (HTML)
File	Description
interactive_3d_scatter.html	Rotatable 3D plot: age × release × damage
interactive_sunburst.html	Drill-down: terrain → equipment → detection
interactive_parallel_coords.html	Multi-dimensional incident comparison
interactive_timeline.html	Animated time-series of incidents by year
📁 Repository Structure
text
CO2-Pipeline-Risk-Assessment-PhD/
│
├── data/
│   ├── raw/                          # Raw PHMSA data
│   └── processed/                    # Engineered features (22 columns)
│
├── notebooks/                        # Jupyter notebooks
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_temporal_analysis.ipynb
│   ├── 03_spatial_analysis.ipynb
│   ├── 04_equipment_analysis.ipynb
│   └── 05_detection_analysis.ipynb
│
├── src/
│   ├── data_loader.py                # Data loading utilities
│   ├── visualizations.py             # All visualization functions
│   ├── risk_metrics.py               # Risk matrix calculations
│   └── ml_features.py                # Feature engineering for ML
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
└── README.md
🚀 Quick Start
bash
# Clone repository
git clone https://github.com/[your-username]/CO2-Pipeline-Risk-Assessment-PhD.git
cd CO2-Pipeline-Risk-Assessment-PhD

# Install dependencies
pip install -r requirements.txt

# Generate all visualizations
python src/main.py

# Generate only proposal figures
python src/visualizations.py --proposal-only
📈 Key Results Tables
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
Correlation Matrix (Selected)
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
🤖 ML Feature Recommendations
Category	Features	Justification
Temporal	age_years, construction_decade, months_since_inspection	First-decade failure peak (0.445 t/mi/yr)
Spatial	terrain_slope, elevation_diff, population_distance	Terrain amplification factor = 1.6×
Equipment	valve_density, weld_age, seam_type	Valves 35% failures; welds largest releases
Detection	scada_present, sensor_density, comms_redundancy	SCADA detects only 20.3%
Suggested Models: Random Forest, XGBoost, Bayesian Network, Isolation Forest, LSTM

🛠️ Dependencies
txt
numpy==1.24.3
pandas==2.0.3
matplotlib==3.7.2
seaborn==0.12.2
scikit-learn==1.3.0
plotly==5.15.0
jupyter==1.0.0
notebook==7.0.0
ipykernel==6.25.0
📄 License
MIT License - see LICENSE file for details.

🙏 Acknowledgments
U.S. PHMSA for public access to pipeline incident data

Satartia, MS incident investigation team

PhD Supervisor and CCS Research Group

📧 Contact
Author: [Your Name]
Institution: [Your University]
Email: [your.email@university.edu]
ORCID: [0000-0000-0000-0000]

PhD Topic: Risk Assessment in the Capture and Transport of CO₂ in CCS Systems

🔄 Citation
bibtex
@misc{yourname2025co2pipeline,
  author = {[Your Last Name], [First Name]},
  title = {CO₂ Pipeline Risk Assessment for CCS Systems: Preliminary Analysis of 121 PHMSA Incidents (1994-2024)},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/[your-username]/CO2-Pipeline-Risk-Assessment-PhD},
  doi = {10.5281/zenodo.xxxxx}
}
✅ Future Work
Bayesian network for risk surface estimation

LSTM for time-series anomaly detection

CFD validation of terrain amplification factor

Interactive Streamlit dashboard

Journal publication

<div align="center">
Built with Python, pandas, matplotlib, seaborn, and plotly

© 2025 | PhD Research | CCS Risk Assessment

</div>
