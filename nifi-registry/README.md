# nifi-registrySetUp-Docker
This will guide you to setup nifi-registry within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the nifi-registry docker image
```shell
docker pull apache/nifi-registry:latest
```
2. Run create nifi-registry-app container using nifi-registry image
```shell
docker run --name nifi-registry-app -p 18080:18080 -d apache/nifi-registry:latest
```
3. Wait for 2-3mins for initialization.
4. Open nifi-registry homepage http://localhost:18080/nifi-registry/

## Usage
1. Start the nifi-registry-app container and wait for 2-3mins
```shell
docker start nifi-registry-app
```
2. Visit the nifi-registry URL: http://localhost:18080/nifi-registry/
3. If you want to edit the configuration of nifi-registry, exec into nifi-registry container
```shell
docker exec -it --user root nifi-registry-app bash
```
4. Stop the nifi-registry-app container
```shell
docker stop nifi-registry-app
``` 

# CleanUp
```shell
docker stop nifi-registry-app
docker rm nifi-registry-app
docker rmi apache/nifi-registry:latest
```
