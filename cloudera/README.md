# clouderaQuickStartSetUp-Docker
This will guide you to setup cloudera quickstart within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the cloudera quickstart docker image
```shell
docker pull cloudera/quickstart:latest
```
2. Run create cloudera-quickstart-app container using cloudera quickstart image
```shell
docker run --name cloudera-quickstart-app \
           --hostname=quickstart.cloudera \
           --privileged=true -t -i \
           -p 8888:8888 -p 7180:7180 -p 4040:4040 \
           cloudera/quickstart:latest /usr/bin/docker-quickstart
docker run --hostname=quickstart.cloudera --privileged=true -p 7180:7180 -p 4040:4040 -p 8888:88888 -t -i cloudera/quickstart /usr/bin/docker-quickstart
```
3. Wait for 2-3mins for initialization.
4. Open cloudera manager http://localhost:7180
4. Get cloudera generated username(copy1) and password(copy2).
```shell
docker logs cloudera-app | grep Generated
```
5. Login with: **User:** (paste1) > **Password:** (paste2) > **LOG IN**

## Usage
1. Start the cloudera-app container and wait for 2-3mins
```shell
docker start cloudera-app
```
2. Visit the cloudera URL: https://localhost:8443/cloudera/, and log in with username and password
3. Stop the cloudera-app container
```shell
docker stop cloudera-app
``` 

# CleanUp
```shell
docker stop cloudera-app
docker rm cloudera-app
docker rmi apache/cloudera:latest
```
