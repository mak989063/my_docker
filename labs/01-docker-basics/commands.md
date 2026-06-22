# Docker Commands Cheat Sheet

## List Images

docker images

## Run a Container

docker run nginx

## Run in Detached Mode

docker run -d nginx

## List Running Containers

docker ps

## List All Containers

docker ps -a

## View Logs

docker logs <container_name>

## Execute Shell in Container

docker exec -it <container_name> sh

## Inspect Container

docker inspect <container_name>

## Stop Container

docker stop <container_name>

## Remove Container

docker rm <container_name>

## Force Remove Container

docker rm -f <container_name>

## Remove Image

docker rmi <image_name>
