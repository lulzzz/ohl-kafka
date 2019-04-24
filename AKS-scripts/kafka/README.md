# Running Kafka on AKS

Make sure to change RG_NAME and CLUSTER_NAME to the correct values if you have an existing cluster.

sh install.sh

This will set up helm, and install a three node Kafka cluster with external access via a public IP. Check the status of the cluster via:
kubectl get po

One all three zookeeper and kafka pods are running, you can get one of the public IPs via:

kubectl get svc

To test out your Kafka cluster on Kubernetes, install kafkacat:
apt-get install kafkacat

And run:

kafkacat -b \<PUBLICIP\>:31090 -L

You should see your three brokers and all topics.