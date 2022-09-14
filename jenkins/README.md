# jenkinsSetUp-Docker
This will guide you to setup Jenkins within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Get Started
## Setup
1. Pull the jenkins docker image
```shell
docker pull jenkins/jenkins:lts-jdk11
```
2. Run create jenkins container using jenkins image
```shell
docker run -d -p 8080:8080 -p 50000:50000 --name=jenkins-app jenkins/jenkins:lts-jdk11
```
3. Open Jenkins **Getting Started** page http://localhost:8080
4. Copy the jenkins initialAdminPassword, paste it Getting Started Page and Click on **Continue**.
```shell
docker exec -it jenkins-app cat /var/jenkins_home/secrets/initialAdminPassword
```
5. Click on **Install suggested plugins**
6. Wait for 15-20 mins to install suggested plugins

## Create First Admin User
1. Provide details as follows(Note: please change the creds as per your requirement)
```console
Username         : admin
Password         : admin
Confirm password : admin
Full name        : Administrator
E-mail address   : admin@test.com
```
2. Click on Save and Continue > Save and Finish > Start using Jenkins

## Usage
1. Start the jenkins container
```shell
docker start jenkins-app
```
2. Stop the jenkins container
```shell
docker stop jenkins-app
``` 

# CleanUp
```shell
docker stop jenkins-app
docker rm jenkins-app
docker rmi jenkins/jenkins:lts-jdk11
```
