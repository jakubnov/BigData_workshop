# Lab1: Import data into Hive tables

## Lab goal: 
Once done, user will be able to upload csv dataset into Hadoop table structures and to work with the table via SQL. There will be comparison when creating table stored in csv and parquet. 

### Step 1: Table creation.
The first step is to know data structure and prepare table for dataset. Go to dedicated database where you want to create the table (and have create access in there) and create table. 

Open Impala: Query -> Editor -> Impala

Example bellow: 

> CREATE TABLE 202002_workshop.jno_sales100k_csv ( <br>
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

<i> It isn't needed to refresh all tables metadata and sometimes it isn't even possible because of lack of permission to all databases.</i>
  
  <u> It's a good custom to refresh tables metadata after each data manipulation within table/tables. </u>
  
Sometimes access though ... isn't possible - usually in situation when user doesn't have access to all folders. Then there is a workaround write exact URL address of database. In this case: https://naczsx012.cz.nonprod:8888/hue/filebrowser/view=/user/hive/warehouse/202002_workshop.db

  
  ### Step 3: Select your data
  At this moment you should be able to see uploaded data in your table. 
  
  > SELECT * FROM 202002_workshop.jno_sales100k_csv; 
  
  <b> At this point you are able to upload any data in csv file into HDFS.  </b>
  
  ### Step 4: Store your data in compresed table. 
  To use csv file format for storing huge amount of data isn't effective and usually serves as the first step of uploading data. In case you want to keep data in HDFS for a longer time (it isn't one time analysis), it's better to use some file format that supports compression - e.g. Parquet. 
  
  Let's repeate proces - Create table query as a first step: 
  
  > CREATE TABLE 202002_workshop.jno_sales100k_parquet <br>
> (region STRING  <br>
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
> stored as PARQUET;  <br>
  
 Once is table succesfully created, migrate data from csv table to parquet ones. 
 
 > INSERT INTO TABLE 202002_workshop.jno_sales100k_parquet SELECT * FROM 202002_workshop.jno_sales100k_csv ; <br> 
 
After this step there is again a need to refresh metadata for this new table: 

> REFRESH 202002_workshop.jno_sales100k_parquet; <br>

And now you can query the data.

> SELECT * FROM 202002_workshop.jno_sales100k_parquet; <br> 

 
 ### Step 5: Compare table sizes
 
 Navigate to File browser and to the tables where when after opening table folder you will see dataset. As you can just see, CSV file is multiple times bigger.  

  
