###### START ZOOKEEPER ##########
zookeeper-server-start.sh config/zookeeper.properties

###### START KAFKA ##########
kafka-server-start.sh config/server.properties

###### CREATING A TOPIC  ##########
## Create , Delete and List
kafka-topics.sh --create  --topic first_topic  --zookeeper localhost:2181 --partitions 1 --replication-factor 1

kafka-topics.sh --zookeeper localhost:2181 --list

kafka-topics.sh --zookeeper localhost:2181 --topic first_topic --describe

kafka-topics.sh --zookeeper localhost:2181 --topic second_topic --delete

###### SEND DATA TO CREATED TOPIC  ##########
## Producer generated data
## Always create a topic before creating a producer

kafka-console-producer.sh --topic first_topic --broker-list localhost:9092

##### VERIFY DATA WAS WRITTEN TO KAFKA BY USING KAFKA CONSOLE CONSUMER ####
## Start a  Console Consumer

kafka-console-consumer.sh  --topic first_topic --bootstrap-server localhost:9092

kafka-console-consumer.sh --topic first_topic  --from-beginning --bootstrap-server localhost:9092

### Start a Console Consumer with Group

kafka-console-consumer.sh --topic first_topic --group my-third-Application --bootstrap-server localhost:9092

##### KAFKA CONSUMER GROUP ######

kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list

#### RESET OFFSET ######
