### **Summary of Data Insights and Implications for Model Choice**

| Observation | Evidence / Finding | Interpretation | Implication for Model Selection |
|--------------|--------------------|----------------|---------------------------------|
| **Most numeric features show weak correlation with target** | Correlation coefficients ≈ 0 | Linear relationship between features and `Histology` is minimal | Linear models (e.g., Logistic Regression) likely underperform |
| **Only `Survival_Rate` shows significant ANOVA difference** | p = 0.009 < 0.05 | Survival rate varies meaningfully across tumor types | This feature is informative for classification |
| **Other numeric features (Age, Tumor_Size, Growth_Rate)** | p > 0.05 | These do not vary significantly across tumor types | They may still contribute when combined in non-linear models |
| **Categorical features mostly show weak association** | Chi-square p-values > 0.05 for most; `MRI_Result` ≈ 0.12, `Family_History` ≈ 0.15 | Categorical variables are weak individual predictors | Must rely on models that can combine multiple weak signals |
| **No high correlation among features** | Heatmap shows low inter-feature correlation | Features are not redundant — each adds some unique information | Safe to use all features without dimensionality reduction |
| **Data standardized (mean=0, std=1)** | Applied `StandardScaler` to numeric features | Ensures fair contribution from all features | Enables scaling-sensitive models like MLP, Naïve Bayes, KNN |
| **Target variable (`Histology`) is multi-class** | Four classes: Glioma, Meningioma, Pituitary, No Tumor | Requires multi-class classification support | Use classifiers that handle 3+ classes natively |

---

### 🎯 **Model Selection Justification**

| Model | Type | Reason for Inclusion | Expected Behavior |
|--------|------|----------------------|-------------------|
| **Decision Tree Classifier** | Non-linear, interpretable | Handles mixed feature types; finds hierarchical rules without needing strong correlations | Baseline non-linear model; provides feature importance |
| **Naïve Bayes (GaussianNB)** | Probabilistic | Works well with weakly correlated features; simple and robust | Fast, interpretable probabilistic baseline |
| **Multi-Layer Perceptron (MLPClassifier)** | Neural Network | Learns complex, non-linear feature interactions | Expected to achieve best performance with standardized data |

---

### 🧩 **Summary Insight**
> The exploratory and statistical analyses reveal that the dataset lacks strong linear separability. Most features individually show weak or no statistical relationship with tumor type, indicating that accurate classification requires algorithms capable of modeling **non-linear, multi-feature interactions**.  
> Therefore, **Decision Tree**, **Naïve Bayes**, and **MLP Classifier** were selected as the most appropriate models.



The exploratory and statistical analyses reveal that the dataset lacks strong linear separability. Most features individually show weak or no statistical relationship with tumor type, indicating that accurate classification requires algorithms capable of modeling non-linear, multi-feature interactions.
Therefore, Decision Tree, Naïve Bayes, and MLP Classifier were selected as the most appropriate models.
