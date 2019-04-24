# How to run:

helm install --name kafka-schema-registry incubator/schema-registry --set kafka.enabled=false,kafkaStore.overrideBootstrapServers=PLAINTEXT://kafka-headless:9092

export POD_NAME=$(kubectl get pods --namespace default -l "app=schema-registry,release=kafka-schema-registry" -o jsonpath="{.items[0].metadata.name}")

kubectl port-forward $POD_NAME 8081


https://github.com/confluentinc/schema-registry