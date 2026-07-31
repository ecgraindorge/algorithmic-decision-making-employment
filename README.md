[README_biased_algorithmic_decision_making.md](https://github.com/user-attachments/files/30605827/README_biased_algorithmic_decision_making.md)
# Biased Algorithmic Decision-Making in AI-Powered Hiring

This repository explores how predictive employment models can reproduce group-patterned differences in employment outcomes. Using American Community Survey (ACS) Public Use Microdata Sample (PUMS) person-level data, the project trains employment prediction models and uses group audits, SHAP, and LIME to examine how model predictions are shaped by demographic, educational, household, disability-related, and service-related variables.

The project is designed as both a technical analysis and a public-facing research artifact. It supports a conference poster on biased algorithmic decision-making in AI-powered hiring and demonstrates how explainable AI tools can make model behavior more visible without assuming that explainability alone solves fairness concerns.

---

## Project Motivation

AI-powered hiring and employment screening systems are often presented as efficient and objective, but predictive models can learn from historical social and labor-market patterns. This project examines that issue using a predictive employment model as a proxy setting for understanding how algorithmic decision-making can reproduce unequal patterns.

The central question guiding this project is:

> When a model predicts employment status, what patterns does it learn, and do prediction gaps persist even when sex is removed as an input feature?

---

## Dataset

This project uses the **American Community Survey Public Use Microdata Sample (ACS PUMS)**. ACS PUMS contains anonymized person-level survey records that allow researchers to examine employment-related outcomes alongside demographic, education, household, disability, and service-related variables.

In this project, the target variable is employment status. The analysis compares models that include and exclude sex as a feature, while retaining sex labels for post-model auditing.

The dataset is not a hiring dataset and does not represent job applicants or actual hiring decisions. Instead, it is used as a labor-market prediction setting to examine how models can encode social and structural patterns.

---

## Repository Structure

```text
biased-algorithmic-decision-making-hiring/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_model_training_and_group_audit.ipynb
│   ├── 03_shap_explainability.ipynb
│   ├── 04_lime_local_explanations.ipynb
│   └── 05_poster_visualizations.ipynb
│
├── figures/
│   ├── actual_employment_by_sex_transparent.png
│   ├── actual_vs_predicted_by_sex_transparent.png
│   ├── predicted_employment_with_vs_without_sex_transparent.png
│   ├── top_14_shap_features_model_includes_sex_transparent.png
│   ├── shap_beeswarm_model_includes_sex_wide_transparent.png
│   ├── top_11_shap_features_model_excludes_sex_transparent.png
│   ├── shap_beeswarm_model_excludes_sex_top11_transparent.png
│   └── lime_local_explanation_poster_clean.png
│
├── poster/
│   └── conference_poster.pptx
│
└── docs/
    └── references.md
```

---

## Notebooks

### 1. Data Preparation

`01_data_preparation.ipynb`

Loads the ACS/PUMS data, prepares the employment target, creates readable labels, reviews missingness, and prepares the modeling dataframe.

### 2. Model Training and Group Audit

`02_model_training_and_group_audit.ipynb`

Trains two employment prediction models:

- **Model A:** includes sex as an input feature
- **Model B:** excludes sex as an input feature

Sex is retained for auditing so predicted employment rates can be compared across groups after model training.

### 3. SHAP Explainability

`03_shap_explainability.ipynb`

Uses SHAP to examine global model behavior. This notebook includes top-feature importance plots and beeswarm plots for both the model that includes sex and the model that excludes sex.

### 4. LIME Local Explanations

`04_lime_local_explanations.ipynb`

Uses LIME to explain one individual prediction. This notebook shows which features push a specific prediction toward “employed” or “not employed.”

### 5. Poster Visualizations

`05_poster_visualizations.ipynb`

Creates poster-ready versions of the final visuals using a consistent color palette, white text, dark notebook previews, and transparent image exports for PowerPoint or poster design.

---

## Methods

This project uses:

- Random Forest classification
- Train/test split with stratification
- Group-level prediction audits
- SHAP global explainability
- LIME local explainability
- Poster-ready data visualization with Matplotlib

The modeling workflow compares prediction patterns across two models: one trained with sex included and one trained with sex removed. This allows the project to examine whether removing a protected attribute eliminates group-patterned differences, or whether other variables may still act as proxies for social and labor-market structures.

---

## Key Takeaways

- Predictive models can learn patterns embedded in historical labor-market data.
- Removing sex from the feature set does not automatically remove group-patterned prediction differences.
- SHAP helps identify which features have the greatest influence on the model overall.
- LIME helps explain how a specific individual prediction is constructed.
- Explainability tools improve transparency, but they do not independently guarantee fairness.
- Responsible use of algorithmic systems requires auditing, governance, and human oversight.

---

## Poster Visual Design

The poster visuals use the following design palette:

```python
POSTER_BG = "#061529"
POSTER_BLUE = "#0393DB"
POSTER_ORANGE = "#F26B21"
POSTER_GREEN = "#2E8B45"
POSTER_RED = "#D13F35"
POSTER_WHITE = "white"
```

Most poster figures are displayed in the notebooks with a dark background for readability, but saved with transparent backgrounds for use in PowerPoint.

---

## How to Run the Project

1. Clone this repository or open the notebooks in Google Colab.
2. Install the required packages:

```bash
pip install -r requirements.txt
```

3. Run the notebooks in order:

```text
01_data_preparation.ipynb
02_model_training_and_group_audit.ipynb
03_shap_explainability.ipynb
04_lime_local_explanations.ipynb
05_poster_visualizations.ipynb
```

The figures will be saved to the `figures/` folder.

---

## Requirements

Core Python packages include:

```text
pandas
numpy
matplotlib
scikit-learn
shap
lime
folktables
```

---

## Suggested Colab Links

After uploading the notebooks to GitHub, replace `YOUR-USERNAME` and `YOUR-REPO` with your GitHub username and repository name.

```markdown
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/github/YOUR-USERNAME/YOUR-REPO/blob/main/notebooks/01_data_preparation.ipynb
)
```

---

## Limitations

This project should be interpreted as a research and teaching demonstration rather than an operational hiring model.

Important limitations include:

- The data come from ACS labor-market survey records, not actual hiring or applicant data.
- The analysis uses binary sex categories available in the dataset, which does not fully represent gender identity.
- Prediction gaps should not be interpreted as causal evidence of discrimination.
- Explainability methods show how models use features, but they do not determine whether a system is fair.
- Removing protected attributes does not necessarily remove proxy variables or structural patterns.

---

## Ethical Framing

This project approaches algorithmic decision-making as a sociotechnical issue. Model behavior is shaped by data, feature choices, organizational context, evaluation decisions, and deployment practices. The goal is not only to improve model transparency, but also to show why technical tools must be paired with leadership, governance, and accountability.

---

## Citation and Attribution

Dataset: American Community Survey Public Use Microdata Sample (ACS PUMS), U.S. Census Bureau.

This repository was created to support a conference poster and research project on biased algorithmic decision-making in AI-powered hiring.
