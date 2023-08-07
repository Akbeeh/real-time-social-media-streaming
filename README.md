# Building a Real-Time Social Media Streaming Pipeline
This small project focuses on the use of Apache Kafka and Python to learn more on event streaming.

Help from https://kafka.apache.org/.

## Overview
In this project, we will build a real-time social media streaming pipeline using Apache Kafka and Python. The pipeline will enable the ingestion and processing of sample social media posts and engagements, empowering us to perform dynamic analyses such as sentiment analysis and engagement metrics calculation.

## Steps followed

### 0. Installation & Setup
Website: https://kafka.apache.org/downloads

```bash
# Setup in our PATH (e.g. in the .bashrc)
export KAFKA_HOME=/path/to/kafka
export PATH=$KAFKA_HOME/bin:$PATH
```

### 1. Start the Kafka environment
```bash
# Start ZooKeeper
apache_kafka_folder/bin/zookeeper-server-start.sh apache_kafka_folder/config/zookeeper.properties

# Start Kafka
apache_kafka_folder/bin/kafka-server-start.sh apache_kafka_folder/config/server.properties
```

### 2. Write a Python script to generate a sample social media data
I use the Python library `faker` to generate fake data.

For more details, go check the [docs](https://faker.readthedocs.io/en/master/) or [GitHub](https://github.com/joke2k/faker/tree/master).

Check the content of `generate_social_media_data.py`.

### 3. Create a Kafka topic to store events
```bash
apache_kafka_folder/bin/kafka-topics.sh --create --topic social_media_stream --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

### 4. Implement the Kafka Producer and Consumer
- **Producer**: those client applications that publish (write) events to Kafka.
- **Consumer**: those that subscribe to (read and process) these events.

Python library `confluent-kafka` is used to create basic clients.
For more details, go check the [docs](https://docs.confluent.io/kafka-clients/python/current/overview.html) or [GitHub](https://github.com/confluentinc/confluent-kafka-python).

Check the content of `kafka_producer.py` and `kafka_consumer.py`.

### 5. Run Python files
- First, generate the social media data.
- Simultaneously, the Kafka scripts in order to see the data ingestion and processing in real-time.
