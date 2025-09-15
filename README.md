# Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains
Hybrid Ensemble Framework For Item Classification And Quantity Forecasting In Construction Supply Chains
<h1><p align="center">ABSTRACT</p></h1>

<p>We propose a hybrid ensemble framework that jointly tackles multi-class item prediction and continuous quantity forecasting in construction supply chains. The architecture uses a two-branch pipeline: a Random Forest classifier for MasterItemNo and a Gradient Boosting regressor for QtyShipped, optionally augmented by a compact 1D-CNN prototype to capture sequence-style features. The workflow begins with robust data cleaning (string→numeric conversions, date decomposition), a shared ColumnTransformer preprocessing pipeline (mean-imputation + scaling for numerics; constant-imputation + one-hot encoding for categoricals), and targeted feature engineering (project duration, price-per-sqft, log transforms) to reduce skew and expose signal in sparse categorical distributions. To handle class sparsity we detect and filter ultra-rare classes to enable stratified splits; quantity outliers are down-weighted via an IQR-based sample weighting scheme. Training follows an ensemble schedule with progress reporting to stabilize convergence, and model diagnostics include enhanced learning curves, normalized confusion matrices focused on top-20 classes, and detailed regression residual analyses. For model selection we introduce a composite metric that blends classification accuracy and weighted F1 with a normalized regression score (1 − MAE / range), producing a single, interpretable comparison score. Experiments on held-out validation and test folds demonstrate improved robustness to outliers and better-calibrated quantity predictions, enabling more reliable inventory decisions and procurement planning.
Keywords
hybrid ensemble; item classification; Quantity Forecasting in Construction Supply Chains; Random Forest; Gradient Boosting; 1D-CNN; feature engineering; sample weighting; class sparsity; composite evaluation metric
</p>

<h1><p>2.5 Summary: Gap Filled by This Work</p></h1>

<p>Existing supply-chain forecasting studies generally treat item identification and quantity prediction as separate problems. For instance, Olszewski et al. [1] apply distinct models to classify order completion and to predict lead times, while Shakir and Modupe [2] evaluate multiple robust regression models (Ridge, LASSO, XGBoost, etc.) for demand forecasting without integrating the two tasks. By contrast, our work introduces a hybrid dual-branch ensemble that jointly handles item classification (MasterItemNo) and quantity regression (QtyShipped). One branch of the model (e.g., a Random Forest) predicts the item class, while the other branch (e.g., a Gradient Boosting regressor) predicts shipped quantities; optional 1D-CNN layers can augment feature extraction in either branch. Training these branches together enables the model to capture interactions between item type and quantity in a unified framework, a capability absent in single-task pipelines. Ensemble techniques like Random Forests and gradient boosting are well established in demand forecasting for their predictive power [3], but their use in a coordinated classification–regression pipeline is novel in the procurement context. Our approach builds conceptually on hybrid pipelines used in other domains [4] but, to our knowledge, is the first to apply such a design to simultaneous item-quantity forecasting in supply chains.
  
Beyond model architecture, this work contributes new interpretability and diagnostic tools tailored to the operational setting. We provide enhanced learning curves, residual-error plots, normalized confusion matrices, and item-class-specific prediction trend figures (Figures 1–5) to analyze performance in depth. For example, the normalized confusion matrices (Fig. 2) reveal which item classes are frequently misclassified, guiding targeted data augmentation or model tuning. The residual plots (Fig. 3) expose biases in quantity predictions across different items, indicating systematic under- or over-forecasting. Item-class-wise trend plots (Figs. 4–5) visualize how predicted quantities compare to actuals over time for each product, highlighting patterns that aggregate metrics would obscure. Such diagnostic visualizations—common in model engineering but seldom reported in supply-chain ML studies—provide practitioners with actionable insight. Prior work in supply-chain forecasting often relies on black-box accuracy metrics or advanced methods like SHAP to interpret models [3], but has not emphasized these classic evaluation plots. Our figures bridge this gap by making model behavior transparent to domain experts, facilitating trust and iterative improvement.
A third novel contribution is the use of a domain-aligned composite metric that blends classification accuracy, weighted F1 score, and normalized MAE. Rather than evaluating the classification and regression outputs separately, we compute a single score reflecting both tasks’ performance. This composite metric is designed to reflect procurement priorities (correct item picks and accurate quantities) and to give managers clear, quantitative feedback. As Zhou et al. discuss, designing composite or domain-specific evaluation metrics can yield more meaningful assessments than generic measures [5]. By combining accuracy and F1 for the item-prediction branch with a normalized MAE for the quantity branch, our metric shows whether a performance improvement is due to better classification or better regression (or both). This makes the feedback more interpretable and actionable for supply-chain decision-makers than reporting standard ML metrics (e.g. separate accuracy and MAE) in isolation.

  In summary, our dual-branch hybrid ensemble and its accompanying diagnostics fill a significant gap in the literature. Unlike previous approaches that treated classification and regression independently [1][2] or focused solely on aggregate forecast accuracy [2][3], our framework unifies both objectives and provides a richer analysis of results. The integration of ensemble methods in a classification–regression pipeline (inspired by multi-task frameworks in other fields [4]) enables more robust, item-specific forecasting. Coupled with the novel interpretability tools and composite performance metric, this work advances supply-chain forecasting by offering a transparent, end-to-end solution aligned with procurement operations.
  
References: [1] Olszewski et al., “Regression models predicting lead times and classification models,” Eur. Res. Stud. J., 2024. [2] Shakir and Modupe, “Demand forecasting in retail supply chains: a regression approach,” Global J. Manage. Bus. Res., 2023. [3] Igarashi et al., “Interpretable supply chain forecasting with SOM, ANN, and SHAP,” Sci. Rep., 2025. [4] Hiremath et al., “Hybrid ML and regression framework for classification and quantification in steel,” Discover Mater., 2025. [5] J. Peng et al., “Time series classification techniques in biomedical applications,” Sensors, 2022.
</p>

<p>Full Paper Article: https://handsonlabs.org/hybrid-ensemble-framework-for-item-classification-and-quantity-forecasting-in-construction-supply-chains/?v=c6a82504ceeb</p>


<h2 align="left"> 
  Fig. 1. Correlation Matrix & Exploratory Data Analysis
  <br>
 <a href="https://github.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/tree/main"><img src="https://raw.githubusercontent.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/refs/heads/main/Fig.%201.%20Correlation%20Matrix%20%26%20Exploratory%20Data%20Analysis.png" alt="Fig. 1. Correlation Matrix & Exploratory Data Analysis" width="1020"></a> 
  <br> 
   <br>
</h2>


<h2 align="left"> 
  Fig. 2. Exploratory Targets & Learning Curves Item Classification
  <br>
 <a href="https://github.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/tree/main"><img src="https://raw.githubusercontent.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/refs/heads/main/Fig.%202.%20Exploratory%20Targets%20%26%20Learning%20Curves%20Item%20Classification.png" alt="Fig. 2. Exploratory Targets & Learning Curves Item Classification" width="1020"></a> 
  <br> 
   <br>
</h2>

<h2 align="left"> 
  Fig. 3. Learning Curves Quantity Regression & Test Set Item Classification
  <br>
 <a href="https://github.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/tree/main"><img src="https://raw.githubusercontent.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/refs/heads/main/Fig.%203.%20Learning%20Curves%20Quantity%20Regression%20%26%20Test%20Set%20Item%20Classification.png" alt="Fig. 3. Learning Curves Quantity Regression & Test Set Item Classification" width="1020"></a> 
  <br> 
   <br>
</h2>

<h2 align="left"> 
 Fig. 4. Test Set Quantity Prediction & Validation Set Item Classification
  <br>
 <a href="https://github.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/tree/main"><img src="https://raw.githubusercontent.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/refs/heads/main/Fig.%204.%20Test%20Set%20Quantity%20Prediction%20%26%20Validation%20Set%20Item%20Classification.png" alt="Fig. 4. Test Set Quantity Prediction & Validation Set Item Classificationn" width="1020"></a> 
  <br> 
   <br>
</h2>

<h2 align="left"> 
 Fig. 5. Validation Set Quantity Prediction & Final Validation and Test Score
  <br>
 <a href="https://github.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/tree/main"><img src="https://raw.githubusercontent.com/tobimichigan/Hybrid-Ensemble-Framework-for-Classification-And-Quantity-Forecasting-In-Construction-Supply-Chains/refs/heads/main/Fig.%204.%20Test%20Set%20Quantity%20Prediction%20%26%20Validation%20Set%20Item%20Classification.png" alt="Fig. 5. Validation Set Quantity Prediction & Final Validation and Test Score" width="1020"></a> 
  <br> 
   <br>
</h2>



<p><h1>8. Discussion: 8.1 Why the approach works</h1>

Figure 1: 

Correlation matrix of numeric features from the project dataset. Our exploratory data analysis revealed strong correlations among features (e.g. invoice total, extended price, area) which guided feature engineering. We generated domain-informed features (log-transformed prices, price per sqft, project duration in days, etc.) to linearize relationships and reduce skew, ensuring features are on comparable scales. As one source notes, feature engineering “transform[s] raw features to improve model performance and accuracy” and “ensure[s] that features with different ranges or units are transformed into a comparable scale so that models can learn effectively”[1]. These transformations stabilized the regression by making the target easier to predict and by preventing any single feature from dominating. Simultaneously, we detected outliers in the shipped-quantity target (using an IQR-based test) and down-weighted extreme values during training (outliers were given weight 0.1 while normal points remained at 1.0[2]). 

In practice, this sample weighting (a form of weighted least squares) prevents a few erratic orders from distorting the fitted regression line, thus improving calibration and robustness. Together, thoughtful feature engineering and outlier weighting yield a more stable model: features encode meaningful structure, and the model is not “pulled” by large errors. This explains why our pipeline achieves good calibration and error rates in validation and test.

<h1>8.2 Operational implications</h1>

The item-and-quantity forecasts from our model can be directly plugged into procurement planning. For example, predicted item+quantity pairs give purchasing teams a prioritized shopping list for upcoming projects, enabling bulk ordering or vendor negotiations. Accurate demand forecasts let procurement maintain optimal inventory levels – avoiding both stockouts and waste. In fact, predictive analytics are known to “maintain optimal inventory levels, reducing waste and avoiding stockouts” by aligning orders with expected usage[3]. In practice, procurement managers could integrate our forecasts into their ERP systems to trigger purchase orders and budget allocations.
At the same time, several risks must be managed. Model predictions are not perfect and come with uncertainty: overestimating quantity could lead to excess inventory and capital tie-up, while underestimating could cause project delays and expedited-costs. Forecasts must therefore be used in concert with human expertise and buffer stocks. Moreover, procurement teams should continually monitor actual usage versus predictions, updating plans if model errors become systematic. In short, item+quantity predictions provide a data-driven starting point for procurement, but prudent teams will always include safety margins and validate model outputs against real-world signals.


<h1>8.3 Limitations </h1>

While the results are encouraging, the approach has several limitations to acknowledge:

- Ultra-rare classes: Some item categories appear only a handful of times (or even once) in the training data. The model cannot reliably learn from these tiny samples, so we must filter or down-weight them. This means forecast accuracy is poor for truly one-off parts, and procurement teams should treat those predictions with caution.

- Covariate shift: The model assumes new projects are similar to past projects. In reality, new construction sites or design changes can shift the distribution of features. If future projects have different characteristics (e.g. atypical sizes, novel materials, external conditions), the model’s performance may degrade because it was trained under a different data distribution[4]. (In machine-learning terms, real-world data is often non-stationary, so distribution shifts can break the model.)

- Seasonal and external factors: The current model does not explicitly capture time effects or external drivers. For example, seasonal demand cycles, sudden material shortages, or policy changes could cause quantities to deviate from predictions. Likewise, macroeconomic conditions or supply chain disruptions are not part of the input data. These unmodeled factors can introduce errors in our forecasts and should be managed (e.g. through rolling reviews of the model or business logic adjustments).
8.4 Future work
Figure 5: Actual vs Predicted Quantity (validation set), colored by error magnitude. The residuals in this plot highlight where the model errs (warmer colors). Several enhancements could improve performance and reliability:
- Temporal/Seasonal features: Incorporate time-series aspects such as month or quarter indicators, lagged demand, or project timeline features. This would help the model learn seasonal patterns or project phases that affect usage.
- Online/Continual learning: Deploy the model in a pipeline that regularly retrains on new data. As new projects complete and actual usage becomes available, the model could update itself, adapting to drift and maintaining calibration over time.
- Hierarchical/multi-task modeling: Use relatedness between items or projects to “share strength.” For example, a Bayesian hierarchical model or multi-task neural network could borrow information across similar product categories or project types. This would help especially for rare items by pooling data from related classes.

- Advanced uncertainty quantification: 
Move beyond point predictions to provide error bounds. Techniques like quantile regression or conformal prediction could give prediction intervals for quantities, so procurement teams see a range (e.g. 10–20 units) rather than a single number. This would explicitly communicate forecast uncertainty and help manage risk in planning.

<h1>9. Conclusion</h1>
    
We addressed the challenge of forecasting item and quantity requirements for construction procurement. Our solution combines an item-classification model with a quantity-regression model, augmented by targeted feature engineering and sample-weighting. 
This approach yielded significant improvements in predictive accuracy and calibration: classification accuracy on common items was high, and quantity forecasts showed low mean absolute error on held-out data. In practical terms, these gains translate into more reliable material planning. Procurement teams can use the predicted item–quantity pairs as a data-informed shopping list, aligning purchases with actual needs and reducing costly overstock or shortages. 
Overall, our model-driven process offers a scalable path to efficient procurement: it automates routine forecasts while still highlighting limitations. In summary, the proposed approach tackles the initial problem by delivering more accurate and stable demand predictions, with clear quantitative benefits (e.g. higher composite scores and lower MAE) and pragmatic value in procurement operations. Future deployment and iterative refinement will further embed this predictive capability into procurement workflows, yielding ongoing cost and efficiency improvements.

<h1>Sources: </h1>

We built on standard ML principles (feature scaling and engineering[1], weighted regression[2]) and industry best practices for predictive procurement[3]. Our discussion of covariate shift and model limits is informed by the well-known phenomenon that real-world data can change over time[4]. The above analysis integrates these insights with our empirical results (Figs. 1–5) to explain the outcomes and chart future steps.
[1] Feature Engineering: Scaling, Normalization and Standardization - GeeksforGeeks
https://www.geeksforgeeks.org/machine-learning/Feature-Engineering-Scaling-Normalization-and-Standardization/
[2] CTAI - CTD Hackathon Algorithm_ Efficient material forecasting 
[3] How Predictive Analytics Transforms Procurement Strategies
https://www.controlhub.com/blog/procurement-predictive-analytics
[4] Data Distribution Shifts and Monitoring
https://huyenchip.com/2022/02/07/data-distribution-shifts-and-monitoring.html

<h1>Acknowledgements</h1>
We acknowledge CTAI Foundation for the dataset and challenge [9], and the contributors at Handsonlabs Software Academy.
</p>


