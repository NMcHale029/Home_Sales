# Home_Sales
### Dependencies
- os
- Spark
- Java
- findspark
- pyspark.sql from SparkSession
- time

### Overview
Home Sales data from <https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv> was read into a dataframe. A temporary view was created from that dataframe, which was used to run several queries.

The temporary table was cached and validated. The cached table was used to run the same query to test for runtime.

The table was also partitioned by date_built, and a temporary table was created for the parquet data. The common query was run using this table and tested for runtime.

Once all queries were run, the table was uncached and validated

### Results
- The original query was run in .618 seconds
- The cached query was run in .363 seconds
- The partitioned query was run in .351 seconds

### Analysis
Caching the temporary table improved the run time of the original query by running in about 59% of the time. If the data set was larger, or the query was more complex, this could save a lot of financial and time resources.

The partitioned query had a similar runtime to the query using caching. It ran in about 57% of the time of the original query. 

It appears that chaching and partitioning have a more than nominal affect on the resources needed to query data.
