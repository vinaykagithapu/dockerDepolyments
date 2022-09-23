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
```
3. Wait for 5-10mins for initialization.
4. Open cloudera manager http://localhost:8888
5. Login with: **Username:** cloudera > **Password:** cloudera > **Sign in**

## Usage
1. Start the cloudera-quickstart-app container and wait for 2-3mins
```shell
docker start cloudera-quickstart-app
```
2. Visit the cloudera URL: http://localhost:8888, and log in with username and password
3. Exec into cloudera-quickstart-app container to run various tools.
```shell
docker exec -it cloudera-quickstart-app bash
```
4. Within the container run spark-shell
```shell
echo "Spark UI: http://localhost:4040/"
spark-shell
```
5. Stop the cloudera-quickstart-app container
```shell
docker stop cloudera-quickstart-app
``` 

# CleanUp
```shell
docker stop cloudera-quickstart-app
docker rm cloudera-quickstart-app
docker rmi cloudera/quickstart
```
