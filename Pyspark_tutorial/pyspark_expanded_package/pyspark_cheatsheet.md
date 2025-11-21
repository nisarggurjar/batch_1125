# PySpark Cheat-sheet

## Quick Setup
- Create SparkSession: `SparkSession.builder.appName('app').master('local[*]').getOrCreate()`
- Stop: `spark.stop()`

## Read/Write
- `spark.read.csv(path, header=True, inferSchema=True)`
- `df.write.parquet(path)`

## Common Transforms
- `df.select('a','b')`, `df.filter(df.a > 0)`, `df.withColumn('c', df.a + 1)`
- `df.groupBy('k').agg({'v':'sum'})`

## Joins
- `df.join(other, on='key', how='left')`
- Broadcast small table: `from pyspark.sql.functions import broadcast; df.join(broadcast(small), 'key')`

## Performance Tips
- Use Parquet/ORC, avoid Python UDFs, prefer pandas_udf for vectorization, tune `spark.sql.shuffle.partitions`.
