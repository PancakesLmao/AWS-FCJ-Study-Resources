#services #serverless
**Amazon Kinesis** is a fully managed, serverless platform on AWS for **real-time data streaming and processing**. It enables you to **ingest**, **buffer**, **process**, and **analyze** large streams of data (like logs, IoT data, clickstreams, videos, and telemetry) in real time.

# Kinesis Services
| Service                    | Type               | Description                                                                                   |
| -------------------------- | ------------------ | --------------------------------------------------------------------------------------------- |
| **Kinesis Data Streams**   | Serverless         | Real-time data ingestion with fine-grained control over shards.                               |
| **Kinesis Data Firehose**  | Serverless         | Fully managed delivery of streaming data to destinations like S3, Redshift, or Elasticsearch. |
| **Kinesis Data Analytics** | Serverless/Compute | Real-time processing using SQL or Apache Flink over streaming data.                           |
| **Kinesis Video Streams**  | Serverless         | Real-time video and audio ingestion and processing.                                           |
# What to keep in mind
## Data retention limit
- **Kinesis Data Streams** retains data by default for 24 hours, extendable to 365 days.
- **Firehose** does not retain data; it delivers it directly to targets.
## Choose the right service
|Need|Use|
|---|---|
|Low-latency + Fine-grain control|**Kinesis Data Streams**|
|Easy delivery to S3/Redshift/Elasticsearch|**Kinesis Firehose**|
|Real-time SQL-based analysis|**Kinesis Data Analytics**|
|Real-time video stream ingestion|**Kinesis Video Streams**|
### Sharding in Data Streams
- [[Shard]]s define capacity: **1 MB/s write** and **2 MB/s read** per shard.
- Over-sharding = cost, under-sharding = throttling.
### Security Best Practices
- Use **KMS** for encryption.
- Enable **CloudWatch** for monitoring.
- Use **IAM roles** and **policies** to control access.
# Cost
### Kinesis Data Streams

| Cost Component     | Price                          |
| ------------------ | ------------------------------ |
| Shard Hour         | $0.015 per shard-hour          |
| Data Ingestion     | $0.014 per GB                  |
| Extended Retention | $0.02 per GB-month             |
| Enhanced Fan-out   | $0.015 per consumer-shard-hour |

### Kinesis Data Firehose

| Cost Component        | Price                               |
| --------------------- | ----------------------------------- |
| Data Ingestion        | $0.029 per GB                       |
| Lambda Transformation | Additional Lambda execution cost    |
| Format Conversion     | Optional conversion pricing applies |

### Kinesis Data Analytics

|Cost Component|Price|
|---|---|
|KPU (Kinesis Processing Unit)|$0.11 per KPU-hour|
|Minimum 1 KPU|Includes 1 vCPU + 4 GB RAM|
|Storage for Checkpoints|Additional S3/storage charges|

### Kinesis Video Streams

|Cost Component|Price|
|---|---|
|Ingestion|$0.0085 per GB|
|Storage|$0.023 per GB-month|
|Playback/Retrieval|$0.011 per GB|
|Media Insights (e.g., Rekognition)|Billed separately by service|
