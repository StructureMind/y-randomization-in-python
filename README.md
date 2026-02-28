# y-randomization-in-python
Iteratively developed Python solution: prototyped, debugged, and optimized for reproducibility and reliability. 
## Overview: 
This repository contains a Y-randomization pipeline implemented for a project. The project focused on QSAR modelling of a specific drug. Y-randomization was performed to assess whether model performance was due to real-SAR or random correlations and to determine its significance. 
## Objective: 
1. To test whether the observed predictive performance of QSAR model was due to real SAR or random correlation.
2. To determine the significance of the results obtained.
## Methodology: 
1. Extract only feature and target columns from the training set, reading directly from the .sd file while maintaining the correct feature-target relationships.
2. Store the original model's r2 score under a variable.
3. The steps below are contained inside a loop for 500 iterations.
   3.1 Shuffle the target column to replace correct pairs with incorrect ones.
   3.2 Build a Partial-Least-Square (PLS) model with 7 components, the features extracted via Step 1, 74 elements and 11 Cross-Validation (CV) folds.
   3.3 Train the model on shuffled dataset with internal cross validation.
4. Components with the best r2_score and q2_score are selected and displayed.
5. The performance of the original model and the shuffled model are compared using their respective r2_scores.
6. p-value is calculated.
## Language Used: 
Python 
## Technologies Used: 
- numpy
- pandas
- matplotlib.pyplot
- seaborn
- sklearn.model_selection
  | cross_val_score
  | KFold
- sklearn.cross_decomposition
  | PLSRegression
- time
- rdkit
  | Chem
- warnings
## Results: 
- The model trained on the original dataset significantly outperformed the models trained on shuffled dataset, indicating that the predictive performance was not due to random correlation.
| Original Model R2: 0.8880
| Randomized Models (500 iterations):
| Mean R2: -0.2917 ± 0.1654
| Range: [-1.3062, 0.1097]
| Better than original: 0/500
- The p-value calculated was 0.002.
## Visualization:
Histogram of performance metrics across shuffled datasets compared to original model. 
<img width="937" height="580" alt="image" src="https://github.com/user-attachments/assets/6487dc8f-dc9f-4e26-b991-f922b3aad96c" />



