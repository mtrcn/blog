---
title: "Partition Parquet File by Date"
date: 2019-04-07
tags: 
  - "dataengineering"
  - "pyspark"
  - "python"
---

The pyspark script below can split one single big parquet file into small parquet files based on `date` column.

<!--more-->

```
from pyspark.sql.functions import col, dayofmonth, month, year

df = #load data frame

dt = col("date").cast("date")
fname = [(year, "year"), (month, "month"), (dayofmonth, "day")]
exprs = [col("*")] + [f(dt).alias(name) for f, name in fname]

(df.select(*exprs).write.partitionBy(*(name for _, name in fname)).mode("overwrite").parquet('output_location'))
```
