# Lab2: Schedule a Hive query

## Lab goal: 
Once done, user will be able to schedule Hive query within Hue with help of Oozie. 

### Step1: Create a table for storing results
It's important to have a table where data from scheduled runs will be stored. Therefore is need to create a table: 

> CREATE TABLE test_jno.scheduler_output <br>
> ( <br>
> INCREMENTAL_ID INTEGER <br> 
> TIMESTAMP 
> ) <br>
> STORED AS PARQUET; 

### Step 2: Create and save a Have query


### Step 3: Schedule query


### Step 4: Check results
First step is to refresh medata in case you didn't add REFRESH databasename.tablename at the end of scheduled script.

Run:
> REFRESH test_jno.scheduler_output; 

Now you are able to select your data in table. Run: 
> SELECT * FROM test_jno.scheduler_output;

