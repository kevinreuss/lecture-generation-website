# Distributed Computing with Apache Spark

Apache Spark is a distributed computing system known for its speed and ease of use in handling large datasets. It offers APIs in Java, Scala, Python, and R, and supports multiple data sources.

## Core Concepts

Spark's ecosystem comprises four components:

1. Spark Core: Basic functionality, including task scheduling and memory management.
2. Spark SQL: Support for structured data and the execution of SQL queries.
3. Spark Streaming: Enables processing of live data streams.
4. MLlib: Machine learning library.
5. GraphX: Graph computation in the data-parallel model.

## Resilient Distributed Datasets (RDDs)

RDDs are immutable, partitioned collections of objects that can be processed in parallel. They're created by loading an external dataset or distributing a set of objects. Here's an example using Python:

```python
data = [1, 2, 3, 4, 5]
distData = sc.parallelize(data)
```

## Transformations and Actions

RDDs support two types of operations:

1. Transformations: Create a new dataset from an existing one. They're lazily evaluated, meaning Spark computes them only in a terminal action. Examples include `map()`, `filter()`, and `reduceByKey()`.

2. Actions: Return a value to the driver program after running a computation on the dataset. Examples include `reduce()`, `collect()`, and `count()`.

Consider the following example:

```python
rdd = sc.parallelize([1, 2, 3, 4, 5])
rddFiltered = rdd.filter(lambda x: x % 2 == 0)  # Transformation
result = rddFiltered.collect()  # Action
```

## Spark SQL

Spark SQL allows you to execute SQL queries on Spark data, and supports various data sources. You can interact with the SQL interface using either SQL or the Dataset API. Here's an example:

```python
peopleDF = spark.read.json("examples/src/main/resources/people.json")
peopleDF.createOrReplaceTempView("people")
sqlDF = spark.sql("SELECT * FROM people")
sqlDF.show()
```

## Spark Streaming

Spark Streaming enables processing of live data streams. Here's a simple example:

```python
ssc = StreamingContext(sparkConf, 1)
lines = ssc.socketTextStream("localhost", 9999)
counts = lines.flatMap(lambda line: line.split(" "))\
              .map(lambda word: (word, 1))\
              .reduceByKey(lambda a, b: a+b)
counts.pprint()
ssc.start()            
ssc.awaitTermination()
```

In this example, we're creating a local StreamingContext with two execution threads and a batch interval of one second. We then connect to a socket on localhost port 9999, and count the words in input streams.