# Customer Analysis

## Roadmap
1. Acquire the data <br>
2. State the question <br>
3. Exploratory Analysis <br>


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
- Statistics <br>
- 