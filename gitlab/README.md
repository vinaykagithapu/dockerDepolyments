# gitlabSetUp-Docker
This will guide you to setup gitlab within Docker


## Requirements
1. Docker([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Linux OS(Ubuntu)

# Getting Started
## Setup
1. Set up the volumes location (Change location based on requirement)
```shell
export GITLAB_HOME=$HOME/gitlab
```
2. Install GitLab using Docker Engine
```shell
docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --name gitlab-app \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  --shm-size 256m \
  gitlab/gitlab-ce:latest
```
3. The initialization process may take a long time(5-10mins). You can track this process with
```shell
docker logs -f gitlab-app
```
4. Get the gitlab intial_admin_password 
```shell
sudo docker exec -it gitlab-app grep 'Password:' /etc/gitlab/initial_root_password
```
5. Visit the GitLab URL: http://localhost , and log in with username **root** and the password
6. Change the root password
```console
Menu > Admin > Latest users > Administrator > Edit > Password > Password confirmation > Save changes
```
7. Login with new password

## Usage
1. Start the gitlab container and wait for 2-3mins
```shell
docker start gitlab-app
```
2. Visit the GitLab URL: http://localhost, and log in with username and password
3. Stop the gitlab container
```shell
docker stop gitlab-app
``` 

# CleanUp
```shell
docker stop gitlab-app
docker rm gitlab-app
docker rmi gitlab/gitlab-ce:latest
sudo rm -r $HOME/gitlab
```
