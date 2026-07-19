# AI Job Impact 2030 — Executive Report

## Executive Summary

The analysis in `AI Job Impact 2030.ipynb` evaluates how artificial intelligence may affect job roles by 2030, using a dataset containing role-level employment attributes such as job title, salary, years of experience, education level, AI exposure, technology growth factors, automation probability, and a labeled risk category.

The notebook performs exploratory data analysis, prepares the data for machine learning, and compares three classification approaches to predict whether a job falls into a Low, Medium, or High AI-impact risk category:

1. Logistic Regression
2. K-Nearest Neighbors
3. Multi-Layer Perceptron Neural Network

The strongest-performing model in the notebook is Logistic Regression, which achieved an F1 score above 99% on the test data. K-Nearest Neighbors also performed extremely well, though slightly below Logistic Regression. The neural network achieved strong but lower performance, with an F1 score slightly above 90%.

The key business conclusion is clear: for this dataset, a simpler and more explainable model outperformed more complex alternatives. This is important for executive decision-making because it suggests that organizations can build practical, interpretable AI workforce risk tools without necessarily relying on opaque or expensive deep learning systems.

---

## Business Context

AI is expected to reshape the labor market by automating tasks, changing productivity expectations, and increasing demand for technical adaptability. For employers, policymakers, educators, and workforce planners, the key challenge is not simply identifying which jobs may be affected, but prioritizing where action is most urgent.

This analysis supports that goal by classifying job roles into risk categories based on indicators such as:

- AI exposure
- Automation probability
- Technology growth factor
- Salary and experience levels
- Education requirements
- Job title characteristics

The intended business value is to help leaders identify which roles may require reskilling, redesign, workforce planning, or strategic investment before AI-driven disruption accelerates.

---

## Data and Analytical Approach

### Dataset

The notebook downloads and loads the Kaggle dataset `AI_Impact_on_Jobs_2030.csv` from the dataset source `khushikyad001/ai-impact-on-jobs-2030`.

The dataset contains a mixture of categorical and numerical variables. The notebook confirms that there are no missing values and that the columns are accessible without naming issues.

### Exploratory Data Analysis

The notebook includes visual exploration using Plotly, including:

- A 3D scatter plot comparing job title, AI exposure index, and risk category
- A bar chart comparing job title, technology growth factor, and risk category

These visuals are useful for identifying how risk is distributed across roles and how technology growth may relate to AI impact.

### Preprocessing

The workflow separates categorical and numerical features, then applies preprocessing using a Scikit-Learn `ColumnTransformer` and pipeline approach.

The target variable is `Risk_Category`, which is encoded for classification. The dataset is split into training and testing data using an 80/20 split with stratification to preserve the distribution of risk categories.

---

## Model Performance Summary

Three models were evaluated.

| Model | Relative Performance | Executive Interpretation |
|---|---:|---|
| Logistic Regression | Best; F1 score above 99% | Best balance of accuracy, simplicity, and explainability |
| K-Nearest Neighbors | Very strong; slightly below Logistic Regression | Accurate but less transparent and potentially less scalable |
| Multi-Layer Perceptron Neural Network | Strong; F1 score slightly above 90% | More complex, but did not outperform simpler methods |

### Key Finding

The Logistic Regression model produced the best results in this notebook. This is especially meaningful because Logistic Regression is easier to interpret, faster to train, less costly to maintain, and generally more transparent than a neural network.

For business leaders, this means a highly effective AI job-risk classification capability can likely be deployed with a relatively simple model, provided the underlying data remains representative and valid.

---

## Strategic Insights

### 1. Simpler Models Can Be Better for Enterprise Decision-Making

The analysis shows that a traditional machine learning model outperformed a neural network. This is a valuable lesson for organizations evaluating AI solutions: model complexity should not be mistaken for business value.

A simpler model can provide:

- Faster deployment
- Easier governance
- Better explainability
- Lower operating cost
- Greater stakeholder trust

### 2. Risk Classification Can Support Workforce Planning

A reliable risk classification model can help organizations segment roles by potential AI impact. This enables leaders to focus investment where it matters most, including:

- Reskilling programs
- Role redesign
- Automation-readiness planning
- Talent acquisition strategy
- Internal mobility initiatives

### 3. High Predictive Accuracy Should Be Validated Carefully

The Logistic Regression and KNN models achieved exceptionally high performance. While this is encouraging, scores above 99% should be interpreted with caution.

One important consideration is whether the target variable, `Risk_Category`, may be derived directly or indirectly from other variables in the dataset such as `AI_Exposure_Index` or `Automation_Probability_2030`. If so, the model may be learning a rule-based relationship rather than discovering a truly generalizable pattern.

Before using this model for real workforce decisions, the organization should validate it on external or newly collected data.

---

## Recommended Business Actions

### 1. Use Logistic Regression as the Initial Production Candidate

Given its superior performance and explainability, Logistic Regression should be the first model considered for operational use.

Recommended next steps:

- Preserve the full preprocessing and modeling pipeline
- Evaluate model coefficients to identify the strongest predictors of risk
- Create a business-facing dashboard showing risk categories by job family, department, or geography

### 2. Conduct External Validation

Before relying on the model for high-stakes workforce decisions, test it against additional data sources.

Examples include:

- Internal HR job architecture data
- Labor market data
- Industry-specific job taxonomies
- Future survey or expert-labeled datasets

This will determine whether the model generalizes beyond the Kaggle dataset.

### 3. Investigate Feature Importance and Potential Leakage

The organization should confirm whether the target risk category was created using variables that are also included as predictors. If the label was created from features such as automation probability or AI exposure, model performance may be inflated.

Recommended checks:

- Review dataset documentation
- Train models with suspected label-derived variables removed
- Compare performance with and without high-risk leakage features
- Use explainability techniques such as coefficient analysis or SHAP values

### 4. Translate Risk Categories into Workforce Interventions

The model should not simply classify jobs; it should drive action.

Suggested interventions by risk level:

| Risk Category | Recommended Action |
|---|---|
| High | Prioritize reskilling, job redesign, automation impact assessment, and transition planning |
| Medium | Monitor closely, provide targeted AI upskilling, and redesign selected workflows |
| Low | Maintain awareness, improve productivity through AI tools, and track changes over time |

### 5. Build an Executive Dashboard

A dashboard would make the analysis more actionable for senior leaders.

Recommended dashboard views:

- Job roles by AI risk category
- Risk distribution across departments or job families
- AI exposure versus automation probability
- Technology growth factor by role
- Workforce segments requiring immediate reskilling
- Scenario planning for 2025, 2027, and 2030

---

## Governance and Risk Considerations

Because workforce AI-risk models can influence strategic decisions about people, governance is essential.

Recommended safeguards:

- Avoid using the model as the sole basis for employment decisions
- Include human review and expert validation
- Monitor for bias across job families, education levels, and salary bands
- Document model assumptions and limitations
- Refresh the data periodically as AI capabilities and labor markets evolve

---

## Limitations

The notebook provides a strong analytical prototype, but several limitations should be addressed before enterprise deployment:

1. The dataset appears to be externally sourced and may not reflect a specific company’s workforce.
2. Extremely high performance may indicate that the target variable is closely related to one or more input variables.
3. Job titles alone may not capture actual task-level exposure to AI.
4. The neural network may require additional tuning for a fairer comparison.
5. The analysis would benefit from model explainability outputs, such as coefficient interpretation or feature importance.

---

## Conclusion

The notebook demonstrates that AI job-impact risk categories can be predicted with very high accuracy using structured job and labor-market attributes. The best-performing model is Logistic Regression, which provides a strong combination of accuracy, transparency, and operational practicality.

For executive stakeholders, the most important takeaway is that AI workforce risk analysis does not need to start with complex black-box models. A well-governed, explainable model can provide immediate value by identifying roles that may require reskilling, redesign, or strategic workforce planning.

The recommended path forward is to validate the model on external or company-specific data, confirm that there is no target leakage, and convert the risk classification framework into an executive workforce planning tool.