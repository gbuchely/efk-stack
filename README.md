# efk-stack

# Running Elasticsearch

$ sudo docker network create efk
$ sudo docker run --network=efk --name elasticsearch -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "cluster.name=docker-cluster" -e "bootstrap.memory_lock=true" -e "ES_JAVA_OPTS=-Xms512m -Xmx512m" --ulimit memlock=-1:-1 -v elasticdata:/usr/share/elasticsearch/data docker.elastic.co/elasticsearch/elasticsearch-oss:6.2.2

# Running Kibana

$ sudo docker run --network=efk --name kibana -d -p 5601:5601 docker.elastic.co/kibana/kibana-oss:6.2.2

# Deploy FluentD
cd ./minikube/custom-daemonset
kubectl create -f fluentd-rbac.yml
kubectl create -f fluentd-config-map
kubectl create -f fluentd-daemonset



################

https://opensource.com/article/18/3/efk-creating-open-source-stack