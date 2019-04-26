# Schema Registry on K8

helm install --name kafka-schema-registry incubator/schema-registry --set kafka.enabled=false,kafkaStore.overrideBootstrapServers=PLAINTEXT://kafka-headless:9092,external.enabled=true,external.servicePort=8081

Wait for LoadBalancer to provision, get public IP:
kubectl get svc

curl -X POST -H "Content-Type: application/vnd.schemaregistry.v1+json" --data '{"schema": "{\"type\": \"string\"}"}'  \<PUBLICIP\>:8081/subjects/Kafka-key/versions

[Schema Registry Confluent Documentation](https://github.com/confluentinc/schema-registry)