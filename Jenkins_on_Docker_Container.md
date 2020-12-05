# Install Jenkins on top of Docker Container

## Create a Jenkins Configuration Folder

`mkdir ~/jenkins-config`

## Create a Jenkins folder to attach volume to Jenkins Docker Container

`mkdir ~/jenkins`

## Change current directory to jenkins-config

`cd jenkins-config`

## Create a docker-compose file in jenkins-config folder to run jenkins in single command

```
version: '3.7'
services:
  jenkins:
    image: jenkins/jenkins:latest
    privileged: true
    user: root
    ports:
      - 8085:8080
      - 50000:50000
    container_name: jenkins
    volumes:
      - ~/jenkins:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
      - /usr/local/bin/docker:/usr/local/bin/docker
```

## Run docker-compose command in detached mode

`docker-compose up -d`

## Jenkins is now up and running on localhost:8085

`<server-ip>:8085`

## To get initial jenkins password

`docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`

## To stop the Jenkins setup, go to 

`cd ~/jenkins-config`

`docker-compose down`
