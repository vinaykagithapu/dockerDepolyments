# sonarqubeSetUp-Docker
This will guide you to setup sonarqube within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the sonarqube docker image
```shell
docker pull sonarqube:latest
```
2. Run create sonarqube-app container using sonarqube image
```shell
docker run --name sonarqube-app -p 9000:9000 -d sonarqube:latest
```
3. Wait for 2-3mins for initialization.
4. Open sonarqube homepage http://localhost:9000/
5. Login into sonarqube using below credentials
```console
username : admin
password : admin
```
6. Update the password.

## Usage
1. Start the sonarqube-app container and wait for 2-3mins
```shell
docker start sonarqube-app
```
2. Visit the sonarqube URL: http://localhost:9000/
3. If you want to edit the configuration of sonarqube, exec into sonarqube container
```shell
docker exec -it --user root sonarqube-app bash
```
4. Stop the sonarqube-app container
```shell
docker stop sonarqube-app
``` 

# CleanUp
```shell
docker stop sonarqube-app
docker rm sonarqube-app
docker rmi sonarqube:latest
```
