# Customer Analysis

## Roadmap
1. Acquire the data <br>
2. State the question <br>
3. Exploratory Analysis <br>
4. Train models
5. Validate model


### 1. Acquire the data
Marketing Customer Value Analysis <br>
https://www.ibm.com/communities/analytics/watson-analytics-blog/marketing-customer-value-analysis/ <br>
<br> 
Customer: unique value per customer <br>
State: Customer's region <br>
Customer Lifetime Value: the difference between the total amount of revenues from a customer and the companies' expenses for this customer. <br>
Response: Customer Response <br>
Coverage: Insurance coverage <br>
Education: Type of education <br>
Effective To Date: The specific date that an insurance policy goes into effect <br>
EmploymentStatus: Employment status <br>
Gender: Customer's gender <br>
Income: Income level
Location Code: environments like rural, urban, etc. <br>
Marital Status: Marital Status <br>
Monthly Premium Auto: Monthly payment for the policy <br>
Months Since Last Claim: Months Since Last Claim<br>
Months Since Policy Inception: months since the beginning of the policy <br>
Number of Open Complaints: Number of current open complaints <br>
Number of Policies: Number of policies <br>
Policy Type: Policy type <br>
Policy: Name of specific policy <br>
Renew Offer Type: Offer type <br>
Sales Channel: Sales Channel
Total Claim Amount: Total amount claimed per customer <br>
Vehicle Class: Vehicle class <br>
Vehicle Size: Vehicle size <br>
>
### 2. State the question
Can we predict the amount claimed by a client? <br>


### 3. Exploratory Analysis

24 columns:  <br>
- 16 object type (categorical)  <br>
- 8 numeric type  <br>
9134 entries <br>
 
- **Missing values** Our dataframe has no missing values<br>

- **Unique values** for each categorical column. <br>

#### Categorical variable
- **Effective To Date** Change the type to ordinal. <br>

- **Drop customer columns** it's not relevant for our model. <br>

- Know the **distribution** of the categories for each variable. <br>

- **Bar plot** for each categorical variable. <br>

#### Numerical Varibale
- **Statistics** <br>
Income: min and q1 it is 0 <br>
Number of Complains: max it's 5 and there is a few complains. <br>
Number of polices: max it 9, and mean it's 2.9. <br>
Total Claim Amount: min it's 0.09 and max it's 2893. <br>

- **Correlation** <br>
The variables do not show much correlation, only 'Monthly Premium Auto' with 'Total Claim Amount' (0.63) and 'Customer Lifetime Value' (0.4). <br>

I try drop 'Monthly Premium Auto' and fit all models with machine learning and the results not show diferences. Conclusion: I keep the column. <br>
>
- **Distribution** <br>
Plot a histogram for income and the distribution. In Customer Lifetime Value, Monthly Premium Auto and Total Claim Amount there are a lots of values in a low level. We have otliers and later try our model without this variables. <br>

- **Total Claim Amount** <br>
Let categorize our variable 'Total Claim Amount' with lables Low, Moderate, High and Very High. <br>

We tried cut only 3 levels(0-IQR1-IQR2-Max), but the most of data was concentrated in one label. We decided cut in 4 levels (0-IQR1-Mean-IQR2-Max). <br>
Low: 0 with values between 0 and IQR 1(272.2582445)<br>
Moderate: 1 with values between IQR 1(272.2582445) and Mean(434.0887943128969) <br>
High: 2 with values between Mean(434.0887943128969) and IQR2 (547.5148387500001) <br>
Very High: 3 with values between IQR2(547.5148387500001) and Max (2893.239678) <br>


### 4. Train models
y (target) = Total Claim Labels <br>

Convert feature Total Claim Amount in class = Total Claim Labels <br>
>
x (data) = rest of our data <br>
<br>
##### Target = Total Claim Label with 3 class <br>
In our target 'Total Claim Amount' convert to 3 labels, most of the data was grouped in class 1, the models' score were very high but the confussion matrix show us that the class 1 not were well classifier. <br>
With this data we tried: <br>
- SVM SVC:  Accuracy SVM: 0.5615763546798029 <br>
- SVM SVC with Robust Scaler: Accuracy: 1.0 <br>
- Logistic Regression: Accuracy: 0.565407772304324 <br>
- Principal Components (n=6): 0.578544061302682 <br>
- Principal Components (n=2): 0.2857142857142857 <br>
- Cross Validation Score: [1., 0.99562124,  0.99452655,  0.99452655, 0.99780822] <br>


##### Target = Total Claim Label with 4 class <br>

- First let's convert them to ordinal data using Pandas' get_dummies. <br>
- Drop Total Claim Amount <br>
- **Logistic Regression**: <br> Accuracy: 0.5199781061850027 <br>
- **Support Vector Machine**: <br>
Grid Search: parameters = 'C':20, 'gamma':'scale', 'coef0':0.0 <br>
Accuracy: Accuracy SVM: 0.3880678708264915 <br>
- **Random Forest Classifier**
Grid Search: parameters = 'n_estimator':50 <br>
Accuracy SVM: 0.9978106185002736 <br>
<br>
Conclusion: Random Forest Classifier with 50 stimators and class weight it's the best model. <br>

### 5. Evaluate model
(/home/miriam/Escritorio/Final-Project-Ironhack/Random-Forest-Confusion_matrix.png?raw=true "Confusion Matrix")
<br>
Cross-validated scores: [0.99606299 0.99868766 0.9993434  0.9986868  0.99868421 0.99934211] <br>
<br>
Classification Report <br>

              precision    recall  f1-score   support

           0       0.88      0.94      0.91       452
           1       0.75      0.84      0.80       593
           2       0.69      0.59      0.63       316
           3       0.90      0.78      0.83       466

   micro avg       0.81      0.81      0.81      1827
   macro avg       0.80      0.79      0.79      1827
weighted avg       0.81      0.81      0.81      1827

### 5. Resolving problems
Nuestro modelo nos da un accuaricy en Random Forest muy alto. Vamos a intentar resolver este problema en varios métodos. <br>
- Eliminar Feature: <br>
Eliminamos Features que puede que no sepamos a la hora de analizar a un cliente: 'Months Since Last Claim', 'Months Since Policy Inception', 'Number of Open Complaints', 'Response'. <br>
<br>
- Eliminamos Customer Lifetime Value, características de clientes que puede que discrimine mis datos. <br>
<br>
Tras estas operaciones mi modelo Random Forest sigue presentando un Accuracy 0.9978106185002736. <br>
<br>
- Probamos comprobar todas las features de cada variable, no vemos ninguna variable que se repita en una columna. <br>
<br>
- Eliminamos columnas: 