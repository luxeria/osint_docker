# osint_docker
Docker images for the OSINT project

## Getting Started

    docker network create -d bridge --subnet 172.123.0.0/24 osint_net

    docker build -t zookeeper https://github.com/luxeria/osint_docker.git:#:zookeeper
    docker build -t kafka https://github.com/luxeria/osint_docker.git:#:kafka

    docker run --net osint_net --ip 172.123.0.10 --detach zookeeper
    docker run --net osint_net --ip 172.123.0.20 --detach kafka

