# Exploring Climate Effects on Mental Health Using Supervised Machine Learning and Explainable AI
This project uses Explainable AI alongside unsupervised and supervised machine learning techniques to explore how climate variables — specifically humidity (q), temperature (t2m), and UV radiation — may be linked to mental health outcomes. The goal is to uncover interpretable patterns and potential climate thresholds that can inform early warning systems and support public health policy.

![mean_value_heatmaps](https://github.com/user-attachments/assets/fac259ba-8c1e-4fdd-b268-ea404f703477)

We began with an unsupervised learning approach to explore whether mental health incidents (treated collectively without category labels) could be grouped based on climate features. Using EMAS data filtered for only mental health-related cases, we focused on the spring and summer months in the UK — typically warmer seasons with temperatures ranging between 15°C and 32°C. Seasonal labels were derived from incident timestamps, and only data from spring and summer were retained. 

For clustering, we excluded the primary clinical impression field to treat all mental health cases as a single group. After removing missing values, we applied Spectral Clustering with K-Means affinity. Clusters were analyzed using mean, min, and max feature values. Results showed that high values in temperature, humidity, and UV often coincided with distinct clusters of mental health incidents. However, overlapping ranges across clusters suggested that interactions between climate variables — not single features alone — help differentiate case patterns. The presence of large clusters also indicated the possibility of common climate conditions driving many mental health cases. Yet, without category-specific labels, we could not identify which mental health types were associated with which climate drivers.


To address this, we adopted a supervised learning strategy to investigate how individual mental health categories respond to climate factors. Recognising the class imbalance and overlap found in the unsupervised analysis, we used a binary classification (One-vs-Rest) framework for each category. SMOTE (Synthetic Minority Over-sampling Technique) was used to generate synthetic samples for the minority class, addressing the imbalance problem. We trained an XGBClassifier per category using stratified train-test splits (80/20) and stored the models generated during training for evaluation and future prediction.

## Feature Importance with SHAP
To interpret model predictions, we used SHAP (SHapley Additive exPlanations), which provides fair and consistent feature attribution, unlike XGBoost’s built-in feature importance metrics. SHAP explains both global trends and individual predictions by assigning impact scores to each feature. For each mental health category, we applied SHAP’s TreeExplainer to our trained models and computed the mean absolute SHAP values. These were visualised using bar plots to reveal which climate features — such as temperature, humidity, or UV — were most influential in each category.

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/8a304519-5ced-4d6a-82fc-e76a1f7544da" alt="feature_importance"></td>
    <td><img src="https://github.com/user-attachments/assets/8db2bcdf-a4b8-4907-a2ee-f2826e5636b7" alt="dependency_plots"></td>
    <td><img src="https://github.com/user-attachments/assets/9f511cac-a2d8-4fb4-9fb4-f74f907eb4c9" alt="dependency_density_plot"></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/6dfd7e80-cf91-4865-a777-a3f9d74cfdf8" alt="feature_importance"></td>
    <td><img src="https://github.com/user-attachments/assets/a854e8b7-ab58-42bc-85f9-630f31a28075" alt="dependency_plots"></td>
    <td><img src="https://github.com/user-attachments/assets/57f49bbb-567c-484b-ae75-506f93875a17" alt="dependency_density_plot"></td>
  </tr>
</table>

## Identifying Climate Thresholds with SHAP
To pinpoint specific climate conditions linked to strong model predictions, we focused on the top 5% of SHAP values (above the 95th percentile) for each feature. We extracted the corresponding climate input values and calculated their min, max, and mean, as well as the mean SHAP value. This analysis identifies critical thresholds where climate features have disproportionate influence, offering practical insight into which environmental conditions most strongly affect mental health outcomes.

### Visualising SHAP and Climate Impacts
**Heatmap of SHAP Impact Values by Category:** We created a heatmap by pivoting SHAP summary values into a category-feature matrix (with renamed variables for clarity). This visual highlights how each climate feature impacts each mental health category, providing an intuitive comparison across outcomes.

![shap_heatmap_combined](https://github.com/user-attachments/assets/0eeb2c41-f50f-4767-be84-7f161061ed81)

**Heatmap of Mean Climate Values by Category:** We also visualized the average values of humidity, temperature, and UV for each mental health category. These heatmaps show the typical climate conditions associated with different mental health incidents based on the EMAS dataset and our model predictions.

![mean_value_heatmaps](https://github.com/user-attachments/assets/9c270d1e-df8b-47d8-a1cf-8f8722da90cd)
