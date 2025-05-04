# Exploring Climate Effects on Mental Health Using Supervised Machine Learning and Explainable AI
This project uses Explainable AI alongside unsupervised and supervised machine learning techniques to explore how climate variables — specifically humidity (q), temperature (t2m), and UV radiation — may be linked to mental health outcomes. The goal is to uncover interpretable patterns and potential climate thresholds that can inform early warning systems and support public health policy.

We began with an unsupervised learning approach to explore whether mental health incidents (treated collectively without category labels) could be grouped based on climate features. Using EMAS data filtered for only mental health-related cases, we focused on the spring and summer months in the UK—typically warmer seasons with temperatures ranging between 15°C and 32°C. Seasonal labels were derived from incident timestamps, and only data from spring and summer were retained.

For clustering, we excluded the primary_clinical_impression field to treat all mental health cases as a single group. After removing missing values, we applied Spectral Clustering with K-Means affinity. Clusters were analyzed using mean, min, and max feature values. Results showed that high values in temperature, humidity, and UV often coincided with distinct clusters of mental health incidents. However, overlapping ranges across clusters suggested that interactions between climate variables—not single features alone—help differentiate case patterns. The presence of large clusters also indicated the possibility of common climate conditions driving many mental health cases. Yet, without category-specific labels, we could not identify which mental health types were associated with which climate drivers.


To address this, we adopted a supervised learning strategy to investigate how individual mental health categories respond to climate factors. Recognizing the class imbalance and overlap found in the unsupervised analysis, we used a binary classification (One-vs-Rest) framework for each category. SMOTE (Synthetic Minority Over-sampling Technique) was used to generate synthetic samples for the minority class, addressing the imbalance problem. We trained an XGBClassifier per category using stratified train-test splits and stored the models for evaluation and future prediction.
Feature Importance with SHAP
To interpret model predictions, we used SHAP (SHapley Additive exPlanations), which provides fair and consistent feature attribution, unlike XGBoost’s built-in importance metrics. SHAP explains both global trends and individual predictions by assigning impact scores to each feature. For each mental health category, we applied SHAP’s TreeExplainer to our trained models and computed the mean absolute SHAP values. These were visualized using bar plots to reveal which climate features—such as temperature, humidity, or UV—were most influential in each category.
Identifying Climate Thresholds with SHAP
To pinpoint specific climate conditions linked to strong model predictions, we focused on the top 5% of SHAP values (above the 95th percentile) for each feature. We extracted the corresponding climate input values and calculated their min, max, and mean, as well as the mean SHAP value. This analysis identifies critical thresholds where climate features have disproportionate influence, offering practical insight into which environmental conditions most strongly affect mental health outcomes.
Visualizing SHAP and Climate Impacts
Heatmap of SHAP Impact Values by Category: We created a heatmap by pivoting SHAP summary values into a category-feature matrix (with renamed variables for clarity). This visual highlights how each climate feature impacts each mental health category, providing an intuitive comparison across outcomes.
Heatmap of Mean Climate Values by Category: We also visualized the average values of humidity, temperature, and UV for each mental health category. These heatmaps show the typical climate conditions associated with different mental health incidents based on the EMAS dataset and our model predictions.

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
