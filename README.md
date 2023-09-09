# Setup

## Start k8s and install helm

## Install Prometheus via helm

helm install prometheus prometheus-community/prometheus --set prometheus-node-exporter.hostRootFsMount.enabled=false

helm repo update

helm install prometheus prometheus-community/prometheus

kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext

## Install grafana via helm

helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

helm install grafana grafana/grafana

kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext

## Jenkins

docker run -d -u root --name jenkins -p 8080:8080 -p 50000:50000 -v ./var/jenkins:/var/jenkins_home jenkins/jenkins:latest

#### password

jenkins/secrets
