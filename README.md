# Decision Tree on Breast Cancer
# Project Overview
This project uses Decision Tree algorithms to classify breast cancer data, improving model performance through techniques like hyperparameter tuning, pruning, and feature engineering.

# Preprocessing Data
- Load Dataset
- Instructions to load the dataset using pandas.

- Understanding Nature and Status of Dataset
- Using value_counts(), set_option, columns.tolist, isnull().sum pandas methods.

- Convert 'Diagnosis' Feature and Splitting Data
  The target variable 'diagnosis' should be converted to binary, then split.

# Building the Model
  Applying Class Weights and Training the Decision Tree
  Trained the Decision Tree with class weights.

# Evaluating the Initial Model
Accuracy: 0.96

Classification Report:

plaintext
            precision    recall  f1-score   support
         0       0.96      0.97      0.97        71
         1       0.95      0.93      0.94        43
  accuracy                           0.96       114
 macro avg       0.96      0.95      0.95       114
weighted avg 0.96 0.96 0.96 114


- Confusion Matrix:
[[69  2]
 [ 3 40]]

# First Improving the Model: Hyperparameter Tuning
-Define the Hyperparameter Grid
    Specify a range of values for max_depth, min_samples_split, min_samples_leaf, and criterion.

Fit the Model
    Fit the GridSearchCV object to the training data.

-Evaluate the Tuned Model
    Use the best parameters to train and evaluate our final model.

-Conclusion of Hyperparameter Tuning
    While the overall accuracy is unchanged, the precision for malignant cases (Class 1) has improved, which is crucial in medical diagnostics. However, the slight   
    decrease in recall for malignant cases should be monitored. Overall, the hyperparameter tuning has refined the model, making it more precise in identifying 
    malignant cases.

# Second Improving the Model: Pruning
- Get the Cost Complexity Pruning Path
- Evaluate Different ccp_alpha Values
- Select Best Pruning
- Apply Best Prune (ccp_alpha) to Our Model
- Results
Accuracy: Initial Model: 0.94, Pruned Model: 0.96

Analysis:
A slight increase in accuracy, indicating that the pruned model generalizes better.

Precision: Class 0 (Benign): Improved from 0.93 to 0.96
           Class 1 (Malignant): Remained the same at 0.95
           Improved precision for Benign cases shows fewer false positives, indicating better model reliability.

Recall: Class 0 (Benign): Remained the same at 0.97
        Class 1 (Malignant): Improved from 0.88 to 0.93
        Increased recall for Malignant cases shows fewer false negatives, which is crucial in medical diagnostics.

F1-Score: Class 0 (Benign): Improved from 0.95 to 0.97
          Class 1 (Malignant): Improved from 0.92 to 0.94
          Higher F1-scores indicate a better balance between precision and recall, making the pruned model more robust.

Confusion Matrix:
    Initial Model: True Negatives: 69, False Positives: 2, False Negatives: 5, True Positives: 38
    Pruned Model: True Negatives: 69, False Positives: 2, False Negatives: 3, True Positives: 40
    The pruned model has fewer false negatives and more true positives for Malignant cases, further confirming its improved performance.

Conclusion of Pruning
    The pruned model shows overall better performance with higher accuracy, precision, recall, and F1-scores. It’s more balanced and robust, making it a valuable tool 
    for medical diagnostics.

# Third Improving the Model: Feature Engineering
- Understanding Feature Importance
- Creating New Features Based on Important Features
- Standardizing Data and Splitting New Data
- Retraining Our Best Model with New Features

- Evaluate the Model
Accuracy: 0.95

Classification Report:

plaintext
            precision    recall  f1-score   support
         0       0.96      0.96      0.96        71
         1       0.93      0.93      0.93        43
  accuracy                           0.95       114
 macro avg       0.94      0.94      0.94       114
weighted avg 0.95 0.95 0.95 114


- **Confusion Matrix**:
[[68  3]
 [ 3 40]]

- Conclusion of Feature Engineering
    Although the difference in performance metrics is minimal, the pruned model performs slightly better. However, it’s worth noting that our feature engineering 
    didn’t significantly degrade the model's performance.

# Final Conclusion
Our best improving method is pruning, as it has the best results and performance.

I like the Prune method.
