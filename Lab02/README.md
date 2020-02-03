# Lab2: Schedule a Hive query

## Lab goal: 
Once done, user will be able to schedule Hive query within Hue with help of Oozie. 

### Step1: Create a table for storing results
It's important to have a table where data from scheduled runs will be stored. Therefore is need to create a table: 

> CREATE TABLE test_jno.scheduler_output <br>
> ( <br>
> Incremental_ID INTEGER, <br> 
> time TIMESTAMP <br> 
> ) <br>
> STORED AS PARQUET; 

Not important in this step, but better to do that - refresh metadata after creation of the table: 

> REFRESH test_jno.scheduler_output; 


### Step 2: Create and save a Have query
Since we have created a table into that result of schedulled query will be saved, we can prepare some sample query. Let's have e.g.

> INSERT INTO test_jno.scheduler_output <br>
> SELECT cast(nvl(max(incremental_id),1)+1 as int), current_timestamp() FROM test_jno.scheduler_output; <br>
> REFRESH test_jno.scheduler_output; <br>

and hit save the query. Have only this query in the query window. 

### Step 3: Schedule query
Open Scheduler - Worflow and create new workflow: drag and drop Hive query

### Step 4: Check results
First step is to refresh medata in case you didn't add REFRESH databasename.tablename at the end of scheduled script.

Run:
> REFRESH test_jno.scheduler_output; 

Now you are able to select your data in table. Run: 
> SELECT * FROM test_jno.scheduler_output;

