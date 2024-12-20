# MapReduce in Big Data Processing

MapReduce is a programming model designed for processing large volumes of data in parallel by dividing the work into independent tasks. It consists of two parts, Map and Reduce.

## Map Function
The Map function takes an input pair and produces a set of intermediate key/value pairs. Let's consider an example where we count the occurrence of words in a set of documents.

```java
public class Map {
    public void map(String key, String value) {
        // key: document name
        // value: document contents
        for (String word : value.split(" ")) {
            emit(word, 1);
        }
    }
}
```
In this example, the map function emits each word along with the value of 1.

## Reduce Function
The Reduce function accepts an intermediate key and a set of values for that key. It merges all intermediate values to create a smaller set of values. 

```java
public class Reduce {
    public void reduce(String key, Iterable<Integer> values) {
        // key: a word
        // values: a list of counted occurrences
        int sum = 0;
        for (int count : values) {
            sum += count;
        }
        emit(key, sum);
    }
}
```
In this example, the reduce function sums all counts emitted for each word and produces an output of word and final count.

## Working Principle
MapReduce operates in three stages, namely Map Stage, Shuffle Stage, and Reduce Stage.

- **Map Stage**: The input data is divided into chunks and a map function is applied to each chunk.
- **Shuffle Stage**: The output from the map function is shuffled to rearrange the data into a collection of <key, value> pairs.
- **Reduce Stage**: The reduce function is applied to the shuffled data to generate the output.

MapReduce’s ability to scale and handle failures provides a robust framework for processing large datasets across a cluster of machines. It abstracts the complexity of distributed processing, fault tolerance, data partitioning, and load balancing.