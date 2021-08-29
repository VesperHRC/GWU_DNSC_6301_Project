# GWU_DNSC_6301_Project
### Training Data

###Data dictionary: 

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
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

Here are the last two sections for the model card.

### Quantitative Analysis
* **Metrics used to evaluate final project**: AUC, Cross Validation, Adverse Impact Ratio (AIR), Confusion Matrix
* **Final Results Metrics**:

     All results were recorded with the following model settings:
     * Estimators: 100
     * Max tree depth: 9
     * Cutoff: .20

| Name | AUC Results |
| ---- | ----------- |
|**Training**| 83.9% |
|**Validation**| 78.1% |
|**Test**| 77.3% |

| Desc | Results |
| ---- | ------- |
|**White proportion**| .726 |
|**Hispanic proportion**| .603 |
|**Black proportion**| .615 |
|**Asian proportion**| .699 |
| | |
|**Male proportion** | .645 |
|**Female proportion**| .689 |

| Desc | AIR Results |
| ---- | ------- |
|**Hispanic-to-White**| .83 |
|**Black-to-White**| .85 |
|**Asian-to-White**| .96 |
|**Female-to-Male**| 1.07 |


* **Charts related to final model**:

<img src=https://user-images.githubusercontent.com/89542514/131179604-8126786d-d2a9-4cba-939d-ed920a6c062f.png width = 300, height = 250>
<img src=https://user-images.githubusercontent.com/89542514/131179280-d07e743f-17f3-4be2-a98e-1dc21b8ddead.png = 500, height = 400>
<img src=https://user-images.githubusercontent.com/89542514/131179378-eca9f66a-b7a8-41ec-8157-dc801ff66139.png = 500, height = 400>
<img src=https://user-images.githubusercontent.com/89542514/131161685-bd5f6226-5386-4450-abb5-1a923e40a418.png width = 250 height = 300>




### Ethical Considerations
* **Potential negative impacts of the model**:
     * Although the model produced acceptable results, there are still potential errors present and must be considered when using the model. These errors could result in false positive or false negative predictions which would negatively impact an individual persons or the financial institution deploying this model. Futhermore, it should be noted that bias and discremination remediation attempts were made but the model does not achieve full parity (proportion and AIR metric results are displayed above). 
    
     
* **Potential uncertainties**:
     * The model relies heavily on the most recent payment status (pay_0) with an importance value greater than 20%. Due to the reliance on this specific variable, any unforeseen financial swings could impact the functional performance of the model. In the event of an economical change with statistical signifigance, the model should be re-evaluated to ensure performance results are at or above what was recorded during initial production launch.   
 
* **Potential unexpected results**:
     * The model will not be maintained or monitored going forward. Due to this, any new data or changes introduced could impact the performance and desired end results of the model. 
