readme.md

### Lab goal: 
Once done, user will be able to use partitioning in tables and also will be able to perform "compaction" in case of tables with many data blocks.

### Step 1: Table creation 

<i> <b> Prerequisities: </b> There is expected to have completed Lab01 because of using tables created within the Lab01 </i> 


> CREATE TABLE 202002_workshop.jno_sales100k_csv_part ( <br>
> Region CHAR(50) <br>
> ,Country CHAR(50) <br>
> ,Item_Type CHAR(50) <br>
> ,Sales_Channel CHAR(50) <br>
> ,Order_Priority CHAR(50) <br>
> ,Order_Date TIMESTAMP <br>
> ,Order_ID INT <br>
> ,Ship_Date TIMESTAMP <br>
> ,Units_Sold INT <br>
> ,Unit_Price FLOAT <br>
> ,Unit_Cost FLOAT <br>
> ,Total_Revenue FLOAT <br>
> ,Total_Cost FLOAT <br>
> ,Total_Profit FLOAT <br>
> ) <br>
> PARTITIONED BY (Part_date BIGINT) <br>
> ROW FORMAT DELIMITED <br>
> FIELDS TERMINATED BY ',' <br>
> STORED AS TEXTFILE <br>
> ; <br>
