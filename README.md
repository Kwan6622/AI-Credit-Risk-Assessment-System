# AI Credit Risk Assessment System

> **Status:** Planning & Development — Version 1.0 (Personal Consumer Loans)

## Overview

**AI Credit Risk Assessment System** is a planned machine learning–powered web application for exploring and estimating credit risk. The project aims to combine data analysis, predictive modeling, model explainability, and a user-friendly interface to support *educational* credit-risk assessments.

The system will be developed incrementally. 
**Version 1.0 focuses exclusively on small personal consumer loans**, such as loans for shopping, household purchases, and everyday personal expenses. Mortgage, auto-finance, and corporate lending modules are possible future extensions and are **not included in the initial scope**.

This project is being built as a practical AI engineering portfolio project, with an emphasis on end-to-end development, reliable evaluation, explainability, and maintainable software architecture.

## Objectives

- Explore and understand the factors associated with consumer loan repayment difficulties.
- Build and compare supervised classification models for credit-risk prediction.
- Evaluate models beyond accuracy, especially on potentially imbalanced datasets.
- Explain model predictions and their key contributing features.
- Develop a web interface for entering supported applicant/loan information and viewing illustrative risk assessments.
- Package the selected model behind an API and document limitations, assumptions, and responsible-use considerations.

## Version 1.0 — Personal Consumer Loan Risk Assessment

**Scope:** Small personal loans for consumer purchases and everyday spending.

**Planned workflow:**

1. A user enters the loan and applicant information supported by the trained model.
2. The backend validates the input and applies the same preprocessing used during training.
3. The trained model returns an estimated risk score or probability aligned with the dataset's label definition.
4. The interface presents the result alongside explanations and relevant financial indicators.
5. The result is clearly framed as an educational risk estimate, **not** a lending approval or rejection decision.

### Potential Input Features

Features will depend on the selected dataset and what is legitimately available at prediction time. Candidate features include:

- Applicant income and income-related indicators
- Loan amount and other available loan characteristics
- Existing financial obligations
- Employment information
- Historical repayment/credit information, where available and appropriate
- Derived financial ratios where supported by reliable data

**Important:** Features that do not exist in the training dataset will not be silently invented or passed into the ML model.

## Data

**Initial candidate:** [Home Credit Default Risk (Kaggle)](https://www.kaggle.com/competitions/home-credit-default-risk/data).

The competition provides consumer-credit application data, a repayment-difficulty target, and several related historical tables. The initial milestone will start with a clearly defined baseline using a suitable subset of available features. Dataset usage will follow applicable license/competition rules.

The target variable's exact meaning, data provenance, population limitations, and potential leakage will be documented before modeling. This is **consumer-credit data, not a dedicated mortgage dataset**.

## Machine Learning Approach

This is primarily a **supervised binary classification** problem.

### Planned Baselines and Candidates

| Model | Purpose |
| --- | --- |
| Logistic Regression | Interpretable baseline |
| Random Forest | Tree-based nonlinear benchmark |
| LightGBM or XGBoost | Gradient-boosted tree candidate, if justified by experiments |

Model selection will be based on reproducible experiments rather than an assumption that a more complex algorithm is always better.

### Planned Evaluation

- Train/validation/test separation and leakage prevention
- ROC-AUC and PR-AUC
- Precision, recall, F1-score, and confusion matrix at selected thresholds
- Probability calibration (when probabilities are displayed)
- Performance checks across relevant groups, subject to the availability and appropriateness of data
- Explainability using appropriate techniques, potentially including SHAP

## Proposed Technology Stack

| Layer | Planned Tools |
| --- | --- |
| Data analysis | Python, Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine learning | Scikit-learn, potentially LightGBM/XGBoost |
| Explainability | SHAP (subject to evaluation) |
| Backend API | FastAPI |
| Frontend | React |
| Testing | Pytest |
| Deployment | Docker (later milestone) |

The stack may evolve as the project develops.

## Development Roadmap

- [ ] **Phase 1 — Problem framing and data exploration:** define the target, inspect the dataset, conduct EDA, and document risks and limitations.
- [ ] **Phase 2 — Baseline modeling:** implement leakage-safe preprocessing and Logistic Regression / Random Forest benchmarks.
- [ ] **Phase 3 — Model evaluation and improvement:** compare models, study class imbalance, calibrate outputs, and analyze explanations.
- [ ] **Phase 4 — API and web application:** expose validated inference through FastAPI and develop a React dashboard.
- [ ] **Phase 5 — Engineering and documentation:** add automated tests, reproducible setup instructions, model versioning, and deployment support.
- [ ] **Future Version 2 — Secured lending:** investigate mortgage/auto loans using domain-appropriate data and separate model definitions.
- [ ] **Future Version 3 — Corporate credit analysis:** investigate business financial distress and lending-specific outcomes using appropriate datasets.

## Repository Structure (Planned)

```text
ai-credit-risk-assessment/
├── data/                 # Local data files (subject to license; not committed by default)
├── notebooks/            # EDA and experimental notebooks
├── src/                  # Data processing, training, and inference code
├── models/               # Model artifacts (managed intentionally)
├── backend/              # FastAPI service
├── frontend/             # React web application
├── tests/                # Automated tests
├── docs/                 # Methodology, results, and limitations
├── requirements.txt      # Python dependencies (to be added)
└── README.md
```

*This tree describes the intended structure, not files already implemented.*

## Responsible Use and Limitations

This project is **for learning, research, and portfolio demonstration only**. Predictions should not be used to make real credit approval, pricing, or adverse-action decisions. Credit-risk models require suitable and representative data, fairness testing, governance, legal review, human oversight, and ongoing monitoring before any real-world use. The system will avoid claiming that historical correlations prove causation.

Public datasets may be outdated, non-representative of Vietnamese borrowers, or collected under different lending policies. Model outputs must be interpreted only within the dataset's documented target definition and limitations. No real personal financial information is needed for demonstrations.

## Project Status

**Current milestone:** Planning Version 1.0 and preparing the dataset, baseline models, and development workflow.

Progress, experimental results, architecture decisions, and setup instructions will be added as features are implemented.

## AI Assistance Declaration

Generative AI tools may be used to support brainstorming, documentation, debugging, and learning during development. Dataset preparation, modeling decisions, evaluation, implementation, and reported results will be reviewed and verified by the project author. AI-generated suggestions will not be presented as independently validated findings.
