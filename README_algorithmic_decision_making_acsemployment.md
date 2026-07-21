# Algorithmic Patriarchy in Predictive Employment Models

This repository contains notebooks that uses the Folktables ACSEmployment dataset to demonstrate how predictive systems can reproduce gendered labor-market patterns.

It uses:

- Public census-derived data from the Folktables ACSEmployment task
- A supervised machine learning model to predict employment status
- Group-level auditing by sex and race
- SHAP for global and local explanation
- LIME for a local explanation example
- A no-sex-feature model to demonstrate how proxy variables can preserve group disparities

## Framing

This is not actual hiring-decision data. Employment status is used as a labor-market proxy for thinking about hiring, screening, recruiting, and career-opportunity algorithms.

The central question is:

> If an algorithm learns from historical labor-market data, what gendered patterns might it reproduce?

## Suggested repository description

A public census-derived employment prediction notebook demonstrating how machine learning models can reproduce gendered labor-market patterns, with SHAP and LIME explanations for ethical AI analysis.

## How to run

Install dependencies:

```bash
pip install -r requirements_algorithmic_patriarchy_acsemployment.txt
```

Then open:

```bash
algorithmic_patriarchy_acsemployment_shap_lime.ipynb
```

## Responsible interpretation

The analysis does not prove that a specific employer discriminated. Instead, it shows how models trained on labor-market data may learn patterns shaped by existing social inequality. SHAP and LIME help make that decision logic more visible, but explainability is not the same as fairness.
