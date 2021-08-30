# GWU_DNSC_6301_Project

### Basic Information

* **Person or organization developing model**: Alpha Balde, alpha13balde@gwu.edu; Ranchen (Vesper) Huang, rhuang2@gwu.edu; Jonathan Schlepp, jonathanschlepp@gwu.edu
* **Model date**: 29 August 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [Team_22_Random_Forest.ipynb](Team_22_Random_Forest.ipynb)


### Intended Use
* **Primary intended uses**: The intended use of this data was to explore the encoded circumstances in determining credit approvals for customers across various categories.
* **Primary intended users**: 6301 Project Team 22.
* **Out-of-scope use cases**: None.

### Training Data

### Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 70% training, 15% validation, 15% test
* **Number of rows in training and validation data**: LIMIT_BAL, 
  * Training rows: 21,000
  * Validation rows: 4,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 4,500
* **State any differences in columns between training and test data**: None

### Model Details
* **Columns used as inputs in the final model**: DELINQ_NEXT
* **Column(s) used as target(s) in the final model**: LIMIT_BAL, PAY_0, PAY_2 - PAY_6', BILL_AMT1 - BILL_AMT6, PAY_AMT1 - PAY_AMT6
* **Type of model**: Random Forests
* **Software used to implement the model**: Python
* **Version of the modeling software**: Python 3.6.9
* **Hyperparameters or other settings of your model**: None

### Quantitative Analysis
* **Metrics used to evaluate final project**: AUC, Cross Validation, Adverse Impact Ratio (AIR), Confusion Matrix
* **Final Results Metrics**:

     All results were recorded with the following model settings:
     * Estimators: 400
     * Max tree depth: 11
     * Cutoff: .20

| Name | AUC Results |
| ---- | ----------- |
|**Training**| 88.5% |
|**Validation**| 78.4% |
|**Test**| 77.4% |

| Desc | Results |
| ---- | ------- |
|**White proportion**| .729 |
|**Hispanic proportion**| .601 |
|**Black proportion**| .617 |
|**Asian proportion**| .706 |
| | |
|**Male proportion** | .641 |
|**Female proportion**| .696 |

| Desc | AIR Results |
| ---- | ------- |
|**Hispanic-to-White**| .82 |
|**Black-to-White**| .85 |
|**Asian-to-White**| .97 |
|**Female-to-Male**| 1.09 |


* **Charts related to final model**:
* **Plot of ariable importance
<img src=https://user-images.githubusercontent.com/89204808/131267384-57a841ec-16f9-4a77-93a3-f478f4f8b864.png width = 500, height = 335>
* **Plot of Tree depths vs. training and validation AUC and AIR
<img src=https://user-images.githubusercontent.com/89204808/131267395-f2c441e0-66b2-4001-9bbb-03f6fe51f0b7.png width= 500, height = 400>
* **Accuracy trend as cutoff increases
<img src=https://user-images.githubusercontent.com/89204808/131267418-37fe34fe-0ca9-4bfc-8f91-6c8155da1a21.png width = 500 height = 600>
* **Grid Research Results
<img src=https://user-images.githubusercontent.com/89204808/131267424-bffe8fcf-fae5-4e91-9ea4-fece2dd7ef54.png width = 500 height = 600>




### Ethical Considerations
* **Potential negative impacts of the model**:
     * Although the model produced acceptable results, there are still potential errors present and must be considered when using the model. These errors could result in false positive or false negative predictions which would negatively impact an individual persons or the financial institution deploying this model. Futhermore, it should be noted that bias and discremination remediation attempts were made but the model does not achieve full parity (proportion and AIR metric results are displayed above). 
    
     
* **Potential uncertainties**:
     * The model relies heavily on the most recent payment status (pay_0) with an importance value greater than 20%. Due to the reliance on this specific variable, any unforeseen financial swings could impact the functional performance of the model. In the event of an economical change with statistical signifigance, the model should be re-evaluated to ensure performance results are at or above what was recorded during initial production launch.   
 
* **Potential unexpected results**:
     * The model will not be maintained or monitored going forward. Due to this, any new data or changes introduced could impact the performance and desired end results of the model. 
