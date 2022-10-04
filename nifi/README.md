# nifiSetUp-Docker
This will guide you to setup nifi within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the nifi docker image
```shell
docker pull apache/nifi:latest
```
2. Run create nifi-app container using nifi image
```shell
docker run --name nifi-app -p 8443:8443 -d apache/nifi:latest
```
3. Wait for 2-3mins for initialization.
4. Open nifi homepage https://localhost:8443/nifi/
5. Get nifi generated username(copy1) and password(copy2).
```shell
docker logs nifi-app | grep Generated
```
6. Login with: **User:** (paste1) > **Password:** (paste2) > **LOG IN**

## Usage
1. Start the nifi-app container and wait for 2-3mins
```shell
docker start nifi-app
```
2. Visit the nifi URL: https://localhost:8443/nifi/, and log in with username and password
3. If you want to edit the configuration of nifi, exec into nifi container
```shell
docker exec -it --user root nifi-app bash
```
4. Stop the nifi-app container
```shell
docker stop nifi-app
``` 

# CleanUp
```shell
docker stop nifi-app
docker rm nifi-app
docker rmi apache/nifi:latest
```
