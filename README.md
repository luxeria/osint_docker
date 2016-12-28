# osint_docker
Docker images for the OSINT project

## Getting Started

    docker network create -d bridge --subnet 172.123.0.0/24 osint_net

    docker build -t zookeeper "github.com/luxeria/osint_docker.git#master:zookeeper"
    docker build -t kafka "github.com/luxeria/osint_docker.git#master:kafka"

    docker run --net osint_net --ip 172.123.0.10 -p 0.0.0.0:2181:2181 --detach zookeeper
    docker run --net osint_net --ip 172.123.0.20 -p 0.0.0.0:9092:9092 --detach kafka

