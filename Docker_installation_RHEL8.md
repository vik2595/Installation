# Simplest way to install Docker on RHEL8 (Red Hat Linux)

## Update system 

`sudo yum update -y`

## Add Docker installation repository into config-manager

`sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo`

`sudo dnf install docker-ce-3:19.03.13-3.el8 -y`

## Start docker by following command

`sudo systemctl start docker`

## Verify Docker installation by 

`docker version`

## Add current user to Docker group to run as non-root user

`sudo usermod -aG docker $USER`

## To change current group to Docker group

`sudo usermod -aG docker $USER`

## Verify changes by 

`docker ps`

## Install Docker-compose

`curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o docker-compose`

`sudo mv docker-compose /usr/local/bin && sudo chmod +x /usr/local/bin/docker-compose`
