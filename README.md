# Kafka Producer

## Requirements:
  - [docker-compose](https://docs.docker.com/compose/install/)

## Run
```sh
$ docker-compose up -d --build
```
## Send custom message
```sh
curl -X POST http://127.0.0.1:4055/confluent-kafka-producer/api/v1/message \
-H "Content-Type: application/json" \
-d "@sample-message1.json"
```

## Checking sent messages
```sh
$ docker-compose exec schema_registry bash
$ kafka-avro-console-consumer\
    --bootstrap-server kafka:9092\
    --property schema.registry.url=http://schema_registry:9052\
    --property print.key=true\
    --from-beginning --topic com.confluent-kafka-producer.producer.TestMessage1
```
