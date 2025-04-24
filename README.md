# Climate & Mental Health: Unsupervised Pattern Discovery
This project uses unsupervised machine learning to explore how climate variables—**humidity (`q`)**, **temperature (`t2m`)**, and **UV radiation (`uvbed`, `uvbedcs`)**—may be linked to mental health cases. The goal is to uncover interpretable patterns and potential climate thresholds that can support early warning systems and inform policy decisions.


<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/c6777132-cc91-469e-8066-559b3baa23e3" alt="feature_importance"></td>
    <td><img src="https://github.com/user-attachments/assets/42952aad-0eb5-4076-8c8b-9398431a8325" alt="dependency_plots"></td>
    <td><img src="https://github.com/user-attachments/assets/d3463516-7c86-469f-9766-a434ff43a2a4" alt="dependency_density_plot"></td>
  </tr>
  <tr>
    <td>Feature Importance</td>
    <td>Dependency Plots</td>
    <td>Dependency Density Plot</td>
  </tr>
</table>


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
