# nexusSetUp-Docker
This will guide you to setup nexus within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Pull the nexus docker image
```shell
docker pull sonatype/nexus3:3.41.1
```
2. Run create nexus-app container using nexus3 image
```shell
docker run -d -p 8081:8081 --name nexus-app sonatype/nexus3:3.41.1
```
3. Wait for 2-3mins for initialization.
4. Open Nexus welcome page http://localhost:8081
4. Get(copy1) nexus initialAdminPassword.
```shell
docker exec -it nexus-app cat /nexus-data/admin.password
```
5. Login: Sign In > Username: admin > Password:(paste1) > Sign In

## Post Configuration
### Setup New Password 
1. Click on **Next > New password: > Confirm password: > Next**
2. **Disable** Disable anonymous access > **Next > Finish**

## Usage
1. Start the nexus-app container and wait for 2-3mins
```shell
docker start nexus-app
```
2. Visit the nexus URL: http://localhost:8081, and log in with username and password
3. Stop the nexus-app container
```shell
docker stop nexus-app
``` 

# CleanUp
```shell
docker stop nexus-app
docker rm nexus-app
docker rmi sonatype/nexus3:3.41.1
```
