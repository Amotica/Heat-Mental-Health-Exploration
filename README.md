# Climate & Mental Health: Unsupervised Pattern Discovery
This project uses unsupervised machine learning to explore how climate variables—**humidity (`q`)**, **temperature (`t2m`)**, and **UV radiation (`uvbed`, `uvbedcs`)**—may be linked to mental health cases. The goal is to uncover interpretable patterns and potential climate thresholds that can support early warning systems and inform policy decisions.
![feature_importance](https://github.com/user-attachments/assets/c6777132-cc91-469e-8066-559b3baa23e3)
![dependency_plots](https://github.com/user-attachments/assets/42952aad-0eb5-4076-8c8b-9398431a8325)
![dependency_density_plot](https://github.com/user-attachments/assets/d3463516-7c86-469f-9766-a434ff43a2a4)


```markdown
## Key Features Overview

| **Temporal Engineering** | **Clustering & Profiling** | **Modeling & Interpretation** |
|--------------------------|-----------------------------|-------------------------------|
| Defines warm months as summer for seasonality analysis. | Uses Spectral Clustering + K-Means to identify mental health patterns linked to climate. | Builds XGBoost model and interprets with SHAP values and decision trees. |
| Filters dataset to focus solely on mental health events. | Profiles clusters and demographic subclusters. | Extracts IF...THEN rules from decision tree for transparency. |
| Removes missing values to ensure model readiness. | Computes cluster-wise climate stats for policy insight. | Identifies climate thresholds using SHAP dependency plots. |

---

## Visualizations

| ![feature_importance](https://github.com/user-attachments/assets/c6777132-cc91-469e-8066-559b3baa23e3) | ![dependency_plots](https://github.com/user-attachments/assets/42952aad-0eb5-4076-8c8b-9398431a8325) | ![dependency_density_plot](https://github.com/user-attachments/assets/d3463516-7c86-469f-9766-a434ff43a2a4) |
|:--:|:--:|:--:|
| *Feature Importance* | *SHAP Dependency Plots* | *Density Plot of SHAP Thresholds* |
```

## Key Features
- **Temporal Feature Engineering**  
  Defines summer months as the warm season to emphasize seasonal climate effects.

- **Targeted Filtering**  
  Focuses exclusively on mental health-related events within the dataset.
- **Missing Data Handling**  
  Removes NaNs to ensure compatibility with models like K-Means and XGBoost.
- **Clustering**  
  Applies Spectral Clustering with K-Means affinity to detect meaningful groupings based on climate inputs.
- **Cluster Profiling**  
  Summarizes cluster-level climate characteristics and explores demographic subclusters (e.g., by sex).
- **Decision Tree Interpretation**  
  Uses decision trees to extract interpretable IF...THEN rules for subcluster classification.
- **Supervised Learning with XGBoost**  
  Builds a predictive model to classify mental health alerts from climate features.
- **SHAP Analysis**  
  Interprets model outputs and identifies key climate thresholds influencing predictions.

## Disclaimer

While climate may play a role in mental health, many other factors—such as genetics, lifestyle, socio-economic status, and healthcare access—also contribute significantly. **This project is exploratory (initially) and not intended for clinical or diagnostic use.**
