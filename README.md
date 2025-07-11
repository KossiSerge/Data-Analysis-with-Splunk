# Splunk-for-Bank-Data-Visualization

### Dataset
The dataset used is available [here](./data/fraud_data.csv)
### About the dataset
The Dataset used is an enriched data of the a dataset randomly generated  by the Fraud team of Commonwealth Bank for the Forage cybersecurity role simulation. This dataset consists of payments from various customers made in different periods and amounts. The feature columns include:  
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

![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/data/Dsh1.png?raw=true)
![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/data/Dsh2.png?raw=true)
![image alt](https://github.com/KossiSerge/Splunk-for-Bank-Data-Visualization/blob/main/data/Dsh3.png?raw=true)


### SPL Queries


#### Fraudulent Transactions Percentage by Month


```spl
index=main sourcetype="fraud-data.csv"
| eval month=case(step==0, "May", step==1, "June", step==2, "July", step==3, "August")
| stats count as totalEvents count(eval(fraud="1")) as totalFraudulentTransac by step, month
| sort step, month
| fields - step
| eval fraudPerc=round((totalFraudulentTransac/totalEvents)*100,2)
```

#### Fraudulent Transactions by Month

```spl
index=main sourcetype="fraud-data.csv" fraud="1"
| eval month=case(step==0, "May", step==1, "June", step==2, "July", step==3, "August")
| stats count by step, month
| sort step
| fields - step
```

#### Age group with the most fraudulent activity by Merchant

```spl
index=main sourcetype="fraud-data.csv" fraud="1" age=1
| stats count by merchant
```

#### Bank_Report_FraudCountbyMerchant

```spl
index=main sourcetype="fraud-data.csv" fraud="1"
| stats count by merchant
| sort -count
```

#### Bank_Report_FraudTrendByCategory

```spl
index=main sourcetype="fraud-data.csv" fraud="1"
| eval month=case(step=0, "May", step=1, "June", step=2, "July", step=3, "August")
| chart count over month by category
```

#### Bank_Report_CountbyCategory

```spl
index=main sourcetype="fraud-data.csv" fraud="1"
| stats count by category
```

#### Fraudulent Transactions by Age Group

```spl
index=main sourcetype="fraud-data.csv" fraud="1"
| eval age_group=case(
    age==0.0, "<=18",
    age==1.0, "19-25",
    age==2.0, "26-35",
    age==3.0, "36-45",
    age==4.0, "46-55",
    age==5.0, "56-65"
) 
| stats count by age_group
| sort -count
```
