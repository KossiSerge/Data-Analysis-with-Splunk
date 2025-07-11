# Splunk-for-Bank-Data-Visualization


### About the dataset
corrige:The Dataset used is an enriched data of the a dataset randomly generated  by the Fraud team of Commonwealth Bank for the Forage cybersecurity role simulation. This dataset consists of payments from various customers made in different periods and amounts. The feature columns include:
Step: The steps represent four months.
0: May
1: June
2: July
3: August
Customer: Customer ID
Age: Categorised age
0.0: <= 18
1.0: 19 - 25
2.0: 26 - 35
3.0: 36 - 45
4.0: 46 - 55
5.0: 56 - 65
Gender: Gender of the customer
F: Female
M: Male
PostcodeOrigin: The postcode of origin/source.
Merchant: The merchant's ID. 
Category: Category of the purchase. 
Amount: Amount of the purchase.
Fraud: Target variable that shows if the transaction is fraudulent - 1 or non-fraudulent - 0.
Note: Dataset was randomly generated and created for your virtual experience.



### Dashboard

![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/Dsh1.png?raw=true)
![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/Dsh2.png?raw=true)
![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/Dsh3.png?raw=true)


### SPL Queries


#### Fraudulent Transactions Percentage by Month

#### Fraudulent Transactions by Month

#### Age group with the most fraudulent activity by Merchant

#### Bank_Report_FraudCountbyMerchant

#### Bank_Report_FraudTrendByCategory

#### Bank_Report_CountbyCategory

#### Fraudulent Transactions by Age

#### Bank_Report_FraudCountbyAgeGroup

