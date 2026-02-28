---

title: "Export MS SQL tables to Parquet Files"
slug: "hello-world"
date: 2019-04-07
tags: 
  - "dataengineering"
  - "mssql"
  - "parquet"
  - "pyspark"
  - "spark"
---

The following code exports MS SQL tables to Parquet files via PySpark. It can be used in tables that do not have an indexed column with the numerical type (int, float, etc.).

<!--more-->

```
import sys
from pyspark.sql.session import SparkSession

def get_spark(jdbc_driver_path):
    return SparkSession.builder.master("local[10]").config("spark.driver.extraClassPath", jdbc_driver_path).getOrCreate()

def get_sql_dataframe(host, database_name, table_name, order_by, upperBound, partition_num):
    return spark.read.format("jdbc")\
        .option("url", "jdbc:sqlserver://{host};databasename={database_name};IntegratedSecurity=true".format(host=host, database_name=database_name))\
        .option("dbtable", "(SELECT ROW_NUMBER() OVER (ORDER BY {order_by}) AS row_num, * FROM {table_name}) as tmp".format(order_by=order_by, table_name=table_name))\
        .option("partitionColumn", "row_num")\
        .option("lowerBound", 0)\
        .option("upperBound", upperBound)\
        .option("numPartitions", partition_num)\
        .load()\
        .drop('row_num')

def get_count(host, database_name, table_name):
    return spark.read.format("jdbc")\
        .option("url", "jdbc:sqlserver://{host};databasename={database_name};IntegratedSecurity=true".format(host=host, database_name=database_name))\
        .option("dbtable", "(SELECT COUNT(*) as row_count FROM {table_name}) as tmp".format(table_name=table_name))\
        .load()\
        .first()['row_count']

def export(sql_df, output_folder):
    sql_df.write.mode("overwrite").parquet(output_folder)

if __name__ == "__main__":
    # Database Configuration
    host = '[Host Name]'
    database_name = '[Database Name]'
    table_name = '[Table Name]'
    order_by = '[Indexed Column] DESC'
    jdbc_driver_path = 'mssql-jdbc-6.4.0.jre8.jar'

    # Output
    output_folder = '[Output Folder]'
    partition_num = 1000

    spark = get_spark(jdbc_driver_path)

    total_count = get_count(host, database_name, table_name)

    print str(total_count) + " rows will be exported."

    sql_df = get_sql_dataframe(host, database_name, table_name, order_by, total_count, partition_num)

    export(sql_df, output_folder)
```
