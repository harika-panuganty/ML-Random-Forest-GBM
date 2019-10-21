# ML-Random-Forest-GBM

This weekly project included running Random Forest (RF) Model and Gradient Boosted Machine (GBM) Model for three Kaggle datasets in R:

1. A large patient readmission dataset https://inclass.kaggle.com/c/predicting-30-day-hospital-readmissions 

2. A medium sized patient laboratory values dataset  https://www.kaggle.com/c/gusto/data 

3. 3. A primate junction splice sequence dataset  https://inclass.kaggle.com/c/cs529-project1/data (significant challenges due to nucleotide format of data). This dataset included three outcome variables (IE, EI and N) therefore there are models for each variation of a combination of the three variables. 

a) RF Model: First changed outcome variable to categorical and assigned 'levels', then trained using R function GLM with TrainControl being five-fold cross validation.The variable mtry is the number of variables available for splitting each tree node, default value is 5. Parameter mtry_grid generates sequences of mtry-2, mtry+2 by 1. The objGrid variable creates a dataframe from all combinations of supplied vectors and factors of mtry_grid. FitControl takes into account the method “cv” and the number 5 which indicates a 5-fold cross validation. Using the trained data, test data was predicted using R function predict() with object being readmission trained model, dataset is the readmission test, and type being ‘prob’. The predicted random forest outcome was derived from the predicted data and the outcome we are looking for. The ‘perf’ model was an roc function that took into account a response and a predictor. AUC and 95% CI was printed to check accuracy of the model.

b) Gradient Boosted Machine: First, I changed the variable ‘outcome’ to factors. The GBM parameters are as follows: n.trees (no. of trees), _lr (learning rate/shrinkage), _in_depth (max no. of splits per tree), _min_obs (min. obs. for tree to stop growing). 

All these parameters were input into the expand.grid function and FitControl takes into account the method “cv” and the number 5 which indicates a 5-fold cross validation. In this training model, the data used is the readmission_train data, method is ‘gbm’, tuneGrid is the objGrid, and trControl is fitControl. Using the trained data, test data was predicted using R function predict() with object being readmission trained model, dataset is the readmission test, and type being ‘prob’. The predicted random forest outcome was derived from the predicted data and the outcome we are looking for. The ‘perf’ model was an roc function that took into account a response and a predictor. AUC and 95% CI was printed to check accuracy of the model.
 
