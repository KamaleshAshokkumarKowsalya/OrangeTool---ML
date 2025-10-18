# Glass Identification Dataset — Team 22

📌 Course: Fundamentals of Artificial Intelligence  
👩‍🏫 Instructor: Alla Anohina-Naumeca  
👥 Team Number: 22  
📆 Academic Year: 2024/2025

---

## Project Overview

This project analyzes the Glass Identification Dataset (UCI Machine Learning Repository) to classify types of glass using classical machine learning and clustering methods. The goal is to support tasks such as forensic identification and material classification by building and evaluating several models and exploring the dataset through EDA and clustering.

---

## Team Members

- Ngoc Bao Tram, Tran (231ADB294)  
- Kamalesh Ashokkumar Kowsalya (221ADB216)  
- Bakhodir Rasulov (231ADB155)

---

## Dataset

- Source: UCI Machine Learning Repository — Glass Identification  
- License: Creative Commons Attribution 4.0 International (CC BY 4.0)  
- Instances: 214  
- Attributes: 9 numerical features + class label  
- Classes: 7 glass types (Class 4 has no samples)

Features:
- Refractive Index (RI)
- Sodium (Na)
- Magnesium (Mg)
- Aluminum (Al)
- Silicon (Si)
- Potassium (K)
- Calcium (Ca)
- Barium (Ba)
- Iron (Fe)

Class distribution (samples):
- 1 — building_windows_float_processed: 70  
- 2 — building_windows_non_float_processed: 77  
- 3 — vehicle_windows_float_processed: 17  
- 4 — vehicle_windows_non_float_processed: 0  
- 5 — containers: 13  
- 6 — tableware: 9  
- 7 — headlamps: 29

---

## Methodology

The project is organized in three main parts:

Part I — Data Analysis
- Data conversion: .dat → .csv
- Exploratory Data Analysis: histograms, boxplots, scatter plots, summary statistics
- Outlier detection/handling: Isolation Forest (5% contamination threshold)
- Feature selection: focused on Si, Al, Na, Ca, Mg based on distributional analysis

Part II — Clustering Experiments
- Hierarchical clustering
  - Linkage: average
  - Distance: Euclidean
  - Cut-off experiments: 1.0, 0.7, 0.5, 0.24
  - Optimal: cut-off 0.5 → 12 clusters (selected configuration)
- K-Means clustering
  - Initialization: k-means++
  - Normalization: enabled
  - Optimal k: 4 (silhouette score: 0.512)

Part III — Classification
Algorithms implemented:
- Random Forest
- Logistic Regression
- Artificial Neural Network (MLP)

Notable hyperparameters and chosen models:
- Random Forest: 100 trees, max depth = 6, 3 attributes per split
- Neural Network: 25 neurons (hidden layer), ReLU activation, Adam solver
- Logistic Regression: L2 regularization, C = 550

---

## Results

Evaluation (test set, aggregated)

| Algorithm         | Precision | Recall | F1-Score |
|-------------------|----------:|-------:|---------:|
| Random Forest     | 0.783     | 0.759  | 0.746    |
| Neural Network    | 0.732     | 0.707  | 0.708    |
| Logistic Regression | 0.613   | 0.672  | 0.636    |

Key takeaways:
- Random Forest performed best overall (highest precision and recall).
- Class imbalance negatively affects performance for minority classes.
- Overlap in feature distributions makes perfect separation difficult.
- Clustering suggests 4 natural groups; hierarchical clustering reveals more fine-grained structure under different cut-offs.

---

## Tools & Technologies

- Orange Data Mining (visual workflows)
- Python (pandas, scikit-learn, numpy, matplotlib/seaborn)

---

## Project Structure

text
├── Data/  
│   └── glass_identification.csv  
├── Code/  
│   ├── preprocessing.py  
│   └── analysis.py  
├── Orange_Workflow/  
│   └── project.ows  
├── Reports/  
│   └── TEAM_22_AI_REPORT.pdf  
└── README.md

---

## How to reproduce / Run the analysis

Example steps
1. Create a virtual environment and install dependencies:
   - python -m venv venv
   - source venv/bin/activate  (or `venv\Scripts\activate` on Windows)
   - pip install pandas numpy scikit-learn matplotlib seaborn joblib

2. Preprocess the data:
   - python Code/preprocessing.py
   - This step should convert the original .dat to CSV (if needed), perform cleaning, outlier detection, and save processed data to `Data/glass_identification.csv`.

3. Run the analysis and modeling:
   - python Code/analysis.py
   - This script performs EDA, clustering, model training, hyperparameter choices described in the report, and outputs evaluation metrics and visualizations.

4. Optionally open the Orange workflow:
   - Open `Orange_Workflow/project.ows` in Orange to inspect the visual pipeline and replicate parts of the analysis.

Notes:
- If your environment or file names differ, update the scripts accordingly.
- The scripts in Code/ are expected to save plots and model artifacts; consult those files for details.

---

## Limitations & Considerations

- The dataset is small (214 instances) and imbalanced — be careful when interpreting performance metrics.
- Class 4 has no samples; models cannot learn this class from the provided dataset.
- Results can vary with different preprocessing choices (scaling, imputation, outlier strategy) and random seeds.
- External tools (DeepSeek, Perplexity AI) were used for parameter search and statistical guidance; results are reported as found during experiments.

---

## References

- UCI Machine Learning Repository — Glass Identification Dataset  
- TEAM_22_AI_REPORT.pdf (detailed project report included in Reports/)  
- Additional online guides and documentation used during the analysis (GeeksforGeeks, scikit-learn docs)

---

## License & Attribution

This project uses data under the Creative Commons Attribution 4.0 International (CC BY 4.0) license. Please provide appropriate credit to the dataset and refer to the UCI repository when reusing data or portions of this analysis.

---

## Contact

For questions about this project, analyses, or reproducibility:
- Kamalesh Ashokkumar Kowsalya — GitHub: @KamaleshAshokkumarKowsalya  
(Other team members can be reached via the course or instructor.)

---
