Hadoop, Hive, Spark, Kafka Docker Compose Setup
Version: 3

This Docker Compose file sets up a multi-container environment for running Apache Hadoop, Hive, Spark, and Kafka services. It includes components like Namenode, Datanode, ResourceManager, NodeManager, Zookeeper, Hive, Hue, JupyterLab, Spark Master, Spark Workers, Kafka, and a Kafka topic creator.
Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Important Information

To initiate the Hive Metastore server, you need to manually start it within the Hive container using the following command, Failure to do so will prevent you from writing Hive tables using Spark and visualizing databases in Hue.
- hive --service metastore

If you do not receive any response while executing any jupyter notebook, please restart the kernel.



Clone the repository:

- git clone https://github.com/your/repository.git
cd repository


Build and run the Docker containers:



- docker-compose up -d


## How to Use:

1- Access localhost:9999 to discover numbered notebooks, starting from "init" to download necessary dependencies.

2- Execute notebooks numbered 1, 2, and 3 for batch processing. Simultaneously, launch notebooks 4 and 5 for streaming processing.

3- After running the batch processing notebooks, open Hue at http://localhost:8888. Use the file explorer to view databases and files.

        Login: admin
        Password: admin

4- Run the PowerBi File to access the dashboard.

### Services

Access services through their respective ports:
- Namenode: http://localhost:9870
- ResourceManager: http://localhost:8088
- Hive Beeline: jdbc:hive2://localhost:10000/
- Hue: http://localhost:8888
- JupyterLab: http://localhost:9999
- Spark Master UI: http://localhost:8080
- Kafka: http://localhost:9092
- HiveMetaStore : http://localhost:9083

-------------------------------------------------------


- Namenode: Apache Hadoop Namenode service with port 9870 exposed.


- Datanode: Apache Hadoop Datanode service.


- ResourceManager: Apache Hadoop ResourceManager service with port 8088 exposed.


- NodeManager: Apache Hadoop NodeManager service.


- Zookeeper: Zookeeper service with port 2181 exposed.


- Hive: Apache Hive service with ports 10000 and 10002 exposed.


- Hue: Hue service with port 8888 exposed.


- JupyterLab: JupyterLab service with ports 9999 and 4040 exposed.


- Spark Master: Apache Spark Master service with ports 8080 and 7077 exposed.


- Spark Worker 1 and 2: Apache Spark Worker services with ports 8081 and 8082 exposed respectively. They depend on the Spark Master.


- Kafka: Apache Kafka service with ports 7203 and 9092 exposed.


- Kafka Topic Creator: Creates a Kafka topic named "crypto" with replication factor 1 and one partition.

Network Configuration

The services are connected to a custom Docker bridge network named "hadoop" with the subnet 172.18.0.0/16.
Volumes

A local volume named "shared-workspace" is created to share data between JupyterLab and Spark services.

Feel free to customize the configurations and adapt them according to your specific needs.

