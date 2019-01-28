docker ps[ -a]              list [running] containers
eval $(docker-machine env)  set docker env variables so docker-compose works
docker-machine ls           list docker VMs
docker-compose up           start containers (uses docker-compose.yml)
docker info                 Basic info (# containers, Memory, ...)
docker images               List all images
docker run -i -t ubuntu /bin/bash   Run interactive shell
docker-compose run web bin/rspec    Run (lale) rspecs
docker-compose run web /bin/bash    Run bash in shell
More:
https://docs.docker.com/v1.8/articles/basics/

------------------

#
# Containers
#

### show docker containers

docker ps # running only
docker ps -a # all containers

### start container

/ host-port:container-port
docker run -p 3000:80 (imagename)

... with env vars

docker run -p 3000:80 -e FOO=bar (imagename)

... give the container a name
--name=active-admin

... with different command
docker run --interactive --tty --entrypoint=/bin/bash (imagename) --login

### delete a container

docker rm -f (containername)

# delete all containers
docker rm $(docker ps -a -q)

### show the logs of a container

docker logs (containername)

### run command on container

docker exec -i -t (containername) (command)
-> command = /bin/bash for a shell

#
# Images
#


# build a docker image

/ run in directory with Dockerfile
docker build -t (imagename) .

-> required when Dockerfile or Gemfile changes

# list images

docker images

# delete images

docker rmi (imagename)

# delete all images
docker rmi $(docker images -q)

# prune unused images
docker image prune

# run one-off command in image
docker run (imagename) ls -lah /core/spec/fixture_files/profiles
(same as start container)

#
# Compose
#

### build an application

docker-compose build

### rebuild an application

1) "light"
docker-compose up --build # with (re)build

2) full rebuild
docker-compose run (servicename) bundle install
docker-compose up --build

### run a command on one service

docker-compose run (servicename) (command)
Example: docker-compose run web rake db:create
- to run one-off commands

### start/stop an application

docker-compose up/down
- will build the application
- will restart the app

### show running containers

docker-compose ps

#
# Network
#

docker network ls
docker network inspect (network_name)
docker inspect (container name)

#
# Swarm
#

# Inspect a service

docker service inspect (servicename) --pretty

# Show how a service is deployed and balanced

docker service ps $service-name

# Show all nodes of the swarm

docker node ls

# Update the image of only one service
docker service update --image (imagename) (servicename)

#
# Docker volumes
#

# List all volumes

docker volume ls

# Inspect volume
docker volume (volume-id)

#
# Clean up system
#

# prune stuff
docker system prune -a

# check docker container file size
qemu-img info /Users/phillip/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/Docker.qcow2