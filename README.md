# kafka-schedule-stream


curl -i -X PUT http://localhost:8083/connectors/datagen_local_01/config  -H "Content-Type: application/json"  -d '{ "connector.class": "io.confluent.kafka.connect.datagen.DatagenConnector", "key.converter": "org.apache.kafka.connect.storage.StringConverter", "kafka.topic": "login-events", "schema.filename": "/tmp/datagen-logintime.avsc", "schema.keyfield": "userid", "max.interval": 1000, "iterations": 10000000, "tasks.max": "1" }'


docker-compose exec broker kafka-console-consumer  --bootstrap-server broker:9092  --topic login-events  --property print.key=true  --value-deserializer "org.apache.kafka.common.serialization.LongDeserializer"  --property key.separator=" : "   --from-beginning  --max-messages 10
