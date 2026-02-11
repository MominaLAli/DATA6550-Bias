# DATA6550-Bias: Exploring Bias in the Adult Income Dataset

## Project Overview

This project investigates bias in the Adult Income dataset (Census Income dataset) through comprehensive analysis of multiple machine learning models. We identify, measure, and propose mitigation strategies for gender and racial bias in income prediction algorithms.

**Key Findings:**
- Males are predicted to earn >$50K at 2.7x the rate of females
- Dataset contains severe demographic imbalances: 67.5% male, 86% White
- Accuracy-fairness trade-off observed across all four models tested
- Random Forest: 85.3% accuracy, 17.8% demographic parity difference
- SVM: 79.3% accuracy, 2.4% demographic parity difference (most fair)

## Dataset

**Source:** UCI Machine Learning Repository - Adult Income Dataset  
**Records:** 48,842 individuals from 1994 U.S. Census  
**Features:** 14 demographic and employment attributes (age, education, occupation, race, gender, hours worked, etc.)  
**Target:** Binary classification - Does annual income exceed $50,000?

## Repository Structure

```
DATA6550-Bias/
├── README.md                           # Project overview and documentation
├── final_report.pdf                    # Complete analysis report with findings
├── Code/                               # Individual contributor code
│   ├── [Teammate1]/                   
│   ├── [Teammate2]/                   
│   └── [Teammate3]/                   
├── Data/                              # Dataset files
│   └── adult.csv                      
└── Analysis/                          # Visualizations and intermediate results
```

## Methodology

### Models Evaluated
1. **Logistic Regression** - Linear baseline model
2. **Decision Tree** - Non-linear interpretable model
3. **Random Forest** - Ensemble method for improved accuracy
4. **Support Vector Machine (SVM)** - Maximum-margin classifier

### Fairness Metrics
- **Demographic Parity Difference:** Difference in positive prediction rates between males and females
- **Equal Opportunity (TPR) Difference:** Difference in true positive rates across gender groups
- **Accuracy:** Traditional classification performance metric

### Analysis Pipeline
1. Data preprocessing and exploratory analysis
2. Demographic bias identification and quantification
3. Model training with 80/20 train-test split
4. Performance evaluation (accuracy, precision, recall, F1)
5. Fairness evaluation across multiple metrics
6. Comparative analysis of accuracy-fairness trade-offs

## Key Results

| Model | Accuracy | Demographic Parity Diff | TPR Diff |
|-------|----------|------------------------|----------|
| Logistic Regression | 80.4% | 0.119 | 0.181 |
| Decision Tree | 80.6% | 0.192 | 0.060 |
| **Random Forest** | **85.3%** | 0.178 | 0.049 |
| **SVM** | 79.3% | **0.024** | **0.047** |

**Interpretation:**
- Random Forest achieves highest accuracy but with significant bias
- SVM demonstrates best fairness performance with acceptable accuracy
- No single model optimizes both accuracy and fairness
- Different fairness definitions yield different "best" models

## Bias Mitigation Strategies

### Data-Level Interventions
- Resampling and reweighting underrepresented groups
- Data augmentation with contemporary demographic data
- Feature engineering to reduce proxy effects

### Model-Level Interventions
- Fairness constraints during training (Fairlearn, AIF360)
- Adversarial debiasing techniques
- Threshold optimization for post-processing

### Process-Level Interventions
- Regular bias auditing with multiple fairness metrics
- Stakeholder engagement in model development
- Transparent documentation (model cards, datasheets)

## Technologies Used

- **Python 3.11+**
- **Libraries:**
  - pandas, numpy - Data manipulation
  - matplotlib, seaborn - Visualization
  - scikit-learn - Machine learning models

## Installation & Usage

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Running the Analysis
```bash
# Clone the repository
git clone https://github.com/[your-username]/DATA6550-Bias.git
cd DATA6550-Bias

# Navigate to your code directory
cd Code/[YourLastName]

# Run Jupyter notebook
jupyter notebook income.ipynb
```

### Reproducing Results
1. Ensure `adult.csv` is in the `Data/` directory
2. Open and run `income.ipynb` sequentially
3. Visualizations will be generated and saved to `Analysis/`
4. Model performance metrics will be displayed in notebook output


## Key Insights

1. **Accuracy is Insufficient:** Traditional accuracy metrics mask significant bias against protected groups
2. **Historical Bias Persists:** Models trained on 1994 data perpetuate outdated gender and racial disparities
3. **Proxy Variables Enable Discrimination:** Removing gender/race features doesn't eliminate bias—occupation and education serve as proxies
4. **Fairness is Context-Dependent:** No universal fairness definition; metric selection requires ethical and legal consideration
5. **Multi-Layered Mitigation Required:** Addressing bias needs interventions at data, model, and process levels

## Future Work

- Intersectional fairness analysis (race × gender interactions)
- Causally-informed debiasing methods
- Temporal bias analysis with updated census data
- Comparison with state-of-the-art fairness-aware algorithms
- Real-world deployment considerations and legal compliance testing


---
