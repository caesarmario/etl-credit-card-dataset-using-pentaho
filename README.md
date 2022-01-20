<h1 align="center"> 💳 ETL Credit Card Data Set 💳 </h1>
<p align="center">using <b>Pentaho Data Integration (PDI)/Kettle ⚙</b><br><br>
.: 📄 Dataset taken from <b><a href="https://www.kaggle.com/rikdifos/credit-card-approval-prediction"> Kaggle </a></b> :.
</p><br>
<p align="center">
  <img src="https://img.shields.io/static/v1?label=%F0%9F%8C%9F&message=If%20Useful&style=style=flat&color=BC4E99" alt="Star Badge"/>
  <a href="https://www.github.com/caesarmario">
    <img src="https://img.shields.io/github/followers/caesarmario?style=social&link=https://www.github.com/caesarmario" alt"GitHub"/>
  </a>
  <a href="https://linktr.ee/caesarmario_">
    <img src="https://img.shields.io/badge/Follow%20My%20Other%20Works-019875?style=flat&labelColor=019875&link=https:/linktr.ee/caesarmario_" alt"Linktree"/>
  </a>
  <!-- <a href="XXX">
    <img src="https://img.shields.io/badge/-Predictioin%20with%20Machine%20Learning%20on%20Kaggle-teal?style=flat&logo=kaggle&logoColor=deepblue&link=XXX" alt="Kaggle Projects"/>
  </a> -->
</p>
<br>

<!-- 
## 📃 Table of Contents:
  - [About Project](#-about-project)
  - [Objectives](#-objectives)
  - [Data Set Description](#-data-set-description)
  - [Connection Configuration](#-connection-configuration)
      - [OLTP](#-oltp-configuration)
      - [OLAP](#-olap-configuration)
  - [ETL Process](#-etl-process)
      - [Application Record](#-application-record)
      - [Credit Record](#-credit-record)
      - [Time Dimension](#-time-dimension)
      - [Credit Card Fact](#-credit-card-fact)
  - [Star Schema](#-star-schema)
  - [Before & After ETL Comparison](#-before--after-etl-comparison)
      - [Application Record](#-application-record-1)
      - [Credit Record](#-credit-record-1)
      - [Time Dimension](#-time-dimension-1)
      - [Credit Card Fact](#-credit-card-fact-1)
<br>

## 🖋 About Project
*   This repository contains files to create data warehouse such as:
    - ETL files using Pentaho Data Integration (PDI)
    - Codes to create OLAP (SQL)
    - Codes to select data from OLTP (SQL)
    - Codes to perform random testing (SQL)

    for credit card applicant. The dataset is provided by <a href="https://www.kaggle.com/rikdifos/credit-card-approval-prediction"><b>Seanny (rikdifos)</b></a>.<br>

*   This project will also create:
    - **2 dimension tables** (Applicant_Dimension and CreditRecord_Dimension), 
    - **Time dimension** (Time_Dimension), and 
    - **1 fact table** (CreditCard_Fact).

    using PDI and Microsoft SQL Server 18.
<br><br>

## 📌 Objectives
*   Perform ETL using PDI for both datasets.
*   Create time dimension using PDI.
*   Create fact table using PDI.
<br><br>

## 🧾 Data Set Description
*   The dataset description can be seen <a href="https://www.kaggle.com/rikdifos/credit-card-approval-prediction/discussion/119320"><b>here</b></a>.
<br><br>


## 🔌 Connection Configuration
```
username: 	sa
pass: 		qwer
```
### 📀🔌 OLTP Configuration
![OLTP Config](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/OLTP_Configuration.png)<br>
### 💿🔌 OLAP Configuration
![OLAP Config](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/OLAP_Configuration.png)<br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>


## ⚙ ETL Process
### 👨‍💼 Application Record
![Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension.png)<br>
#### ▶ Table Input Configuration
![Table Input - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/1%20-%20Table%20Input.png)
   - Importing application table from OLTP. <br>
#### ▶ Sort Rows Configuration
![Sort Rows - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/2%20-%20Sort%20Rows.png)
   - Sort data based on applicant ID. <br>
#### ▶ Unique Rows Configuration
![Unique Rows - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/3%20-%20Unique%20Rows.png)
   - Filter duplicate applicant ID. <br>
#### ▶ Replace in String Configuration
![Replace in String - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/4%20-%20Replace%20in%20String.png)
   - Replace some values to make it easier to understand. <br>
#### ▶ Add Constants Configuration
![Add Constants - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/5%20-%20Add%20Constants.png)
   - Add new columns with constant date (October 1, 2021). <br>
#### ▶ Calculator Configuration
![Calculator - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/6%20-%20Calculator.png)
   - Calculate DOB and date of applicant start working based on current date (October 1, 2021).
   - Calculate age of applicant based on current year (2021). <br>
#### ▶ Filter Rows Configuration
![Filter Rows - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/7%20-%20Filter%20Rows.png)
   - Filter applicant data which has null values.
   - Filter applicant data who is less than 21 y.o. <br>
#### ▶ Add Sequence Configuration
![Add Sequence - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/8%20-%20Add%20Sequence.png)
   - Adding Index Applicant (to replace ID as primary key). <br>
#### ▶ Select Values Configuration
![Select Values - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/9%20-%20Select%20Values.png)
   - Select columns that will entered OLAP. <br>
#### ▶ Table Output Configuration
![Table Output - Application](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Applicant_Dimension/10%20-%20Table%20Output.png)
   - Exporting application table to OLAP (Application Dimension). <br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>

### 💶 Credit Record
![Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension.png)<br>
#### ▶ Table Input Configuration
![Table Input - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/1%20-%20Table%20Input.png)
   - Importing credit record table from OLTP. <br>
#### ▶ Sort Rows Configuration
![Sort Rows - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/2%20-%20Sort%20Rows.png)
   - Sort data based on applicant ID. <br>
#### ▶ Add Constants Configuration
![Add Constants - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/3%20-%20Add%20Constants.png)
   - Add new columns with constant date (October 1, 2021). <br>
#### ▶ Calculator Configuration
![Calculator - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/4%20-%20Calculator.png)
   - Calculate loan payment's month based on current date (October 1, 2021). <br>
#### ▶ Add Sequence Configuration
![Add Sequence - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/5%20-%20Add%20Sequence.png)
   - Adding CreditRecord_ID (to replace Applicant ID as primary key). <br>
#### ▶ Select Values Configuration
![Select Values - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/6%20-%20Select%20Values.png)
   - Select columns that will entered OLAP. <br>
#### ▶ Table Output Configuration
![Table Output - Credit Record](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditRecord_Dimension/7%20-%20Table%20Output.png)
   - Exporting application table to OLAP (Credit Record Dimension). <br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>

### ⌚ Time Dimension
![Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension.png)<br>
#### ▶ Generate Rows Configuration
![Generate Rows - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/1%20-%20Generate%20Rows.png)
   - Generate a column with specific date (January 1, 2016). <br>
#### ▶ Add Sequence Configuration
![Add Sequence - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/2%20-%20Add%20Sequence.png)
   - Add row with sequence from 1 to 99999. <br>
#### ▶ Calculator Configuration
![Calculator - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/3%20-%20Calculator.png)
   - Caluclating start date with sequence data to make next date (ex: January 2, 2016; January 3, 2016)
   - Creating new columns (Day, Months, and Year). <br>
#### ▶ Data Grid Configuration
![Data Grid - Time_1](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/4%20-%20Data%20Grid.png)<br>
![Data Grid - Time_2](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/4%20-%20Data%20Grid_2.png)
   - Creating month number and month name. <br>
#### ▶ Stream Lookup Configuration
![Stream Lookup - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/5%20-%20Stream%20Lookup.png)
   - Combine 'Month' from Calculator node to 'No_Month' from Data Grid node. <br>
#### ▶ Modified JavaScript Value Configuration
![Modified JavaScript - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/6%20-%20Modified%20JavaScript.png)
   - Creating time ID using JavaScript code. <br>
#### ▶ Select Values Configuration
![Select Values - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/7%20-%20Select%20Values.png)
   - Select columns that will entered OLAP. <br>
#### ▶ Table Output Configuration
![Table Output - Time](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Time_Dimension/8%20-%20Table%20Output.png)
   - Exporting time dimension to OLAP. <br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>


### 💳 Credit Card Fact
![Credit Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact.png)<br>
#### ▶ Table Input (Credit Record) Configuration
![Table Input CR - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/1%20-%20Table%20Input%20(CreditRecord%20Dimension).png)
   - Importing Credit Record dimension from OLAP. <br>
#### ▶ Table Input (Application) Configuration
![Table Input Application - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/2%20-%20Table%20Input%20(Application%20Dimension).png)
   - Importing Application dimension from OLAP. <br>
#### ▶ Stream Lookup 1 Configuration
![Stream Lookup 1 - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/3%20-%20Stream%20Lookup%201.png)
   - Join both dimension tables based on applicant ID. <br>
#### ▶ Filter Rows Configuration
![Filter Rows - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/4%20-%20Filter%20Rows.png)
   - Filter applicant ID that doesn't exists in both tables. <br>
#### ▶ Table Input (Time) Configuration
![Table Input Time - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/5%20-%20Table%20Input%20(Time%20Dimension).png)
   - Importing Time dimension from OLAP. <br>
#### ▶ Stream Lookup 2 Configuration
![Stream Lookup 2 - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/6%20-%20Stream%20Lookup%202.png)
   - Join application & credit record dimension with time dimension. <br>
#### ▶ Replace in String 1 Configuration
![Replace in String 1 - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/7%20-%20Replace%20in%20String%201.png)
   - Replace C, X, 0 with 'Good Debt' (C: loan for that month is already paid; X: no loan for that month; 0: loan is 1 to 29 days overdue). 
   - Replace 1, 2, 3, 4, 5 with 'Bad Debt' (1: loan is 30 to 59 days overdue; 2: loan is 60 to 89 days overdue; 3: loan is 90 to 119 days overdue; 4: loan is 120 to 149 days overdue; 5: loan is more than 150 days overdue)<br>
#### ▶ Calculator Configuration
![Calculator - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/8%20-%20Calculator.png)
   - Creating 2 copies from 'Status' column ('Good_Debt' and 'Bad_Debt').
#### ▶ Replace in String Configuration
![Replace in String - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/9%20-%20Replace%20in%20String%202.png)
   - Good_Debt: Good Debt will be change to 1, while Bad Debt will be change to 0
   - Bad_Debt: Good Debt will be change to 0, while Bad Debt will be change to 1
#### ▶ Get System Info Configuration
![Get System Info - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/10%20-%20Get%20System%20Info.png)
   - To create date & time when ETL was performed. <br>
#### ▶ Select Values Configuration
![Select Values - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/11%20-%20Select%20Values.png)
   - Select columns that will entered OLAP. <br>
#### ▶ Table Output Configuration
![Table Output - Fact](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/CreditCard_Fact/12%20-%20Table%20Output.png)
   - Exporting fact table to OLAP. <br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>

## ⭐ Star Schema
*   Star schema generated using Power BI
![Star Schema](https://github.com/caesarmario/ETL-credit-card-dataset-using-pentaho/blob/main/Screenshots/Star_Schema_PBI.PNG)<br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>

## 👀 Before & After ETL Comparison
*   This section will show the data structure before & after ETL.
### 👨‍💼 Application Record
![Applicant_1](https://github.com/caesarmario/data-warehouse-credit-card-applicant-using-pentaho/blob/main/Screenshots/Before%20%26%20After/Applicant_1.png)<br>
![Applicant_2](https://github.com/caesarmario/data-warehouse-credit-card-applicant-using-pentaho/blob/main/Screenshots/Before%20%26%20After/Applicant_2.png)<br>

### 💶 Credit Record
![Credit Record](https://github.com/caesarmario/data-warehouse-credit-card-applicant-using-pentaho/blob/main/Screenshots/Before%20%26%20After/Credit%20Record.png)<br>

### ⌚ Time Dimension
![Time Dimension](https://github.com/caesarmario/data-warehouse-credit-card-applicant-using-pentaho/blob/main/Screenshots/Before%20%26%20After/Time%20Dimension.png)<br>

### 💳 Credit Card Fact
![Credit Card Fact](https://github.com/caesarmario/data-warehouse-credit-card-applicant-using-pentaho/blob/main/Screenshots/Before%20%26%20After/Credit%20Card%20Fact.png)<br>

[![](https://img.shields.io/badge/back%20to%20top-%E2%86%A9-blue)](#-table-of-contents)
<br><br>

--> 
## 🙌 Support me!

👉 If you find this project useful, **please ⭐ this repository 😆**!

---

👉 _More about myself: <a href="https://linktr.ee/caesarmario_"> here </a>_
