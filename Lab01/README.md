# Lab1: Import data into Hive tables

## Lab goal: 
Once done, user will be able to upload csv dataset into Hadoop table structures and to work with the table via SQL. There will be comparison when creating table stored in csv and parquet. 

### Step 1: Table creation.
The first step is to know data structure and prepare table for dataset. Go to dedicated database where you want to create the table (and have create access in there) and create table. 

Example bellow: 

> CREATE TABLE test_jno.sales100k_csv ( <br>
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

After hitting a RUN button you should be able see Success information under the query. 

### Step 2: Import data
As a next step when table is created it's need to upload data file on HDFS. Go to File Browser and locate to database (usually path: /user/hive/warehouse/databasename.db) and you should be able to see all existing tables within the database. Table created in the step before should be among them. Table in HDFS is presented as folder - open that folder. In here you should be able see table content. 

Upload your csv file into the table folder. 

Once uploaded run refresh table's metadata: 

> REFRESH databasename.tablename; 

<i> It isn't needed to refresh all tables metadata and sometimes it isn't even possible because of lack of permission to all databases.<i/>
  
  <u> It's a good custom to refresh tables metadata after each data manipulation within table/tables. </u>
  
  ### Step 3: Select your data
  At this moment you should be able to see uploaded data in your table. 
  
  > SELECT * FROM test_jno.sales100k_csv; 
  
  <b> At this point you are able to upload any data in csv file into HDFS.  </b>
  
  
