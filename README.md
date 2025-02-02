## Machine Learning Classification - Wine Quality Prediction


## A. Data Assessment Process   
### A1. Original Dataset Summary:
- Total number of records: 1559
- Total number of features: 12
- Numeric type features: 11 **['fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar', 'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH', 'sulphates', 'alcohol']**
- Categorical type features: 1 **['quality']**
- For machine learning applications **'quality'** feature is the target variable (dependent) and the other 11 features are input (independent).

### A2. Features Description:
| S.NO | Feature               | Description                                                                              |
|:----:| :---                  | :---                                                                                     |
| 1.   | fixed acidity         | Acids that are always present                                                            |
| 2.   | volatile acidity      | Gaseous acids with high values leave an unpleasant vinegar taste                         |
| 3.   | citric acid           | A preservative added in small quantity to increase acidity and for freshness and flavor  |
| 4.   | residual sugar        | The amount of sugar left after fermentation                                              |
| 5.   | chlorides             | The amount of salt present in the wine                                                   |
| 6.   | free sulfur dioxide   | It prevents growth of microbes and oxidation of the wine                                 |
| 7.   | total sulfur dioxide  | The amount of free and bound forms of SO2                                                |
| 8.   | density               | Higher density wines are sweet in taste                                                  |
| 9.   | pH                    | Acidity level of the wine                                                                |
| 10.  | sulphates             | An additive to wine which is antimicrobial and antioxidant                               |
| 11.  | alcohol               | The amount of alcohol present in wine                                                    |
| 12.  | quality               | It indicates the quality of the wine                                                     |
|      |                       |                                                                                          |

### A3. Data Issues:
#### a. Dirty Data (Low quality):
- Completeness: No missing values.
  
- Validity: 240 duplicate observations.

- Accuracy: No inaccuracy issues.

- Consistency: No consistency issues.

#### b. Messy Data (Untidy / Structural):
- No structure related issues.


## B. Data Pre-Processing Results
- Numeric type features: 11 **['fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar', 'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH', 'sulphates', 'alcohol']**
- Categorical type features: 1 **['quality']**
- Total records: 1359
- Data splitting in Train, Validation, and Test sets.
- Finally, the data sets are saved in the CSV and PKL files for further analysis and ML modelling.


## C. Conclusions / Insights of Exploratory Data Analysis
- Outliers: present in the range of 0.08 to 9.23 %.
- Skewness: present in the range of 0.04 to 5.52 and mostly moderate to high for many features.
- There are total six categories for target categorical feature, where label value 5 has occured 491 times.
- Numerical features exhibit a low to moderate correlation among them.
- Features contributing for low quality wines: **[pH, chlorides, volatile acidity, total sulfur dioxide, density, free sulfur dioxide]**
- Features contributing for high quaity wines: **[alcohol, sulphates, fixed acidity, citric acid, residual sugar]**


## D. Feature Engineering
- Target feature 'quality' is categorized as low (3,4,5) and high (6,7,8) for the given labels.
- Data imabalance issues is treated with 'SMOTE' oversampling techique.
- Outliers handling techiques are used to bring the data in suitable range for model building.
- Feature transformation (Yeo-Johnson) technique to make data in Gaussian distribution form.
- Multi-collinearity is checked in the dataset with VIF.
- Feaures are treated with scaling (StandardScaler) technique to make models converge faster.
- Top K most significant features are selected using SelecteKBest technqiue with mutual_info_classif.


## E. Model Building and Hyper Parameter Tuning
- List of models compared: **[Logistic Regression, KNeighborsClassifier, SVC, DecisionTreeClassifier, BaggingClassifier, RandomForestClassifier,
  GradientBoostingClassifier, HistGradientBoostingClassifier, XGBClassifier]**.
- Hyper-Parameter Tuning: GridSearchCV with StratifiedKFold using ML pipelines.


## F. Best Model Results
- **GradientBoostingClassifier (learning_rate=0.01, max_depth=5, n_estimators=200, subsample=0.5, random_state=46)**
- StratifiedKFold(n_splits=10, random_state=46, shuffle=True), Cross Validation Score : 77.2358 %, dataset size : (1230,12)
- Accuracy Score on Validation Data : 75.0 %, dataset size : (100,12)
- Accuracy Score on Test Data : 76.0 %, dataset size : (100,12)


## G. Production Model
- **GradientBoostingClassifier (learning_rate=0.01, max_depth=5, n_estimators=200, subsample=0.5, random_state=46)**
- StratifiedKFold(n_splits=10, random_state=46, shuffle=True), Cross Validation Score : 76.3831 %, dataset size : (1334,12)
- Accuracy Score on Test Data : 77.0 %, dataset size : (100,12)


## H. Gradio App Development  
- Available under 'GR_APP' folder.
- Gradio app inside the Jupyter Notebook file
- App accepts the inputs from the user through the UI interface, performs the logic using production model, and displays the prediction as output.
- The user can try out some examples to see the app's working.
