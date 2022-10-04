# mysqlSetUp-Docker
This will guide you to setup mysql within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the mysql docker image
```shell
docker pull mysql:latest
```
2. Run create mysql-app container using mysql image
```shell
docker run --name mysql-app -e MYSQL_ROOT_PASSWORD=Mysql@123 -p 3306:3306 -d mysql:latest
```
3. Wait for 2-3mins for initialization.
4. Login to mysql with password "Mysql@123"
```shell
mysql -h 127.0.0.1 -u root -p 
```
5. Or Get mysql-app container IP address(copy1) and login to mysql with password "Mysql@123".
```shell
docker inspect mysql-app | grep -i ipaddress
mysql -h (paste1) -u root -p
```

## Usage
1. Start the mysql-app container and wait for 2-3mins
```shell
docker start mysql-app
```
2. Login to mysql with password "Mysql@123"
```shell
mysql -h 127.0.0.1 -u root -p 
```
3. If you want to edit the configuration of mysql, exec into mysql container
```shell
docker exec -it --user root mysql-app bash
```
4. Stop the mysql-app container
```shell
docker stop mysql-app
``` 

# CleanUp
```shell
docker stop mysql-app
docker rm mysql-app
docker rmi apache/mysql:latest
```
