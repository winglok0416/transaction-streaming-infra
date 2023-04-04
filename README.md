This repository is to provide a Docker environment to start the Kafka, Zookeeper and Spark containers for the system.

### Environment
OS: MacOS or Ubuntu 18

Dependencies:
Docker
Docker Compose

### Steps
1. Spin up containers
```
sudo docker-compose up -d
```
2. Verify containers
```
sudo docker ps
```
3. Execute Bash of Spark container (mac: transaction-streaming-infra-spark-1)
```
sudo docker exec -it transaction-streaming-infra_spark_1 /bin/bash
```
4. Copy necessary jars to classpath of Spark
```
cp /test-files/jars/* /opt/bitnami/spark/jars
```
5. Open another terminal and Execute Bash of Kafka container (mac: transaction-streaming-infra-kafka-1)
```
sudo docker exec -it transaction-streaming-infra_kafka_1 /bin/bash
```
6. Create topic by running
```
/opt/bitnami/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --topic transaction --create --partitions 3 --replication-factor 1
```