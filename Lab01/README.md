# Lab1: Import data into Hive table

## Goal: Once done, user will be able to upload csv dataset into Hadoop table structures and to work with the table via SQL. There will be comparison when creating table stored in csv and parquet. 

### Step 1: Table creation.
The first step is to know data structure and prepare table for dataset. Go to dedicated database where you want to create the table (and have create access in there) and create table. 

Example bellow: 

> CREATE TABLE test_jno.sales100k ( <br>
> Region CHAR(50)  <br>
> ,Country CHAR(50) <br>
> ,Item_Type CHAR(50) <br>
> ,Sales_Channel CHAR(50) <br>
> ,Order_Priority CHAR(50) <br>
> ,Order_Date TIMESTAMP  <br>
> ,Order_ID INT <br>
> ,Ship_Date TIMESTAMP <br>
> ,Units_Sold INT <br>
> ,Unit_Price FLOAT <br>
> ,Unit_Cost FLOAT <br>
> ,Total_Revenue FLOAT <br>
> ,Total_Cost FLOAT <br>
> ,Total_Profit FLOAT <br>
> ) <br>
> ROW FORMAT DELIMITED <br>
> FIELDS TERMINATED BY ',' <br>
> STORED AS TEXTFILE <br>
> ; <br>
> 

end of example
