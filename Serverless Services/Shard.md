#concepts
https://stackoverflow.com/questions/56514871/what-is-shards-in-kinesis-data-stream
# What is shard in Amazon Kinesis
A **shard** is a uniquely identified sequence of data records in a stream. 
A **stream** is composed of one or more shards, each of which provides a fixed unit of capacity. Each shard can support up to 5 transactions per second for reads, up to a maximum total data read rate of 2 MB per second and up to 1,000 records per second for writes, up to a maximum total data write rate of 1 MB per second (including partition keys). The data capacity of your stream is a function of the number of shards that you specify for the stream. The total capacity of the stream is the sum of the capacities of its shards.

A shard has two purposes:
- A certain amount of capacity/throughput
- An ordered list of messages