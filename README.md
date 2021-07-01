# DockerTests

## See docker info:
	docker info
## See all containers:
	docker ps -a
## Stop a container (0 exit code - SIGTERM then SIGKILL):
	docker stop <container_name>
## Kill a container (137 exit code - SIGKILL):
	docker kill <container_name>
## Remove container:
	docker rm <container_name>
## See all images:
	docker images -a
## Remove image:
	docker image rm <image_name>
## Create image:
	docker build -f Dockerfile . -t <image_name>:latest
## Delete all containers
	docker rm $(docker ps -a -q)
## Delete all images
	docker rmi $(docker images -q)
## See logs from a container:
	docker logs <container_name>
## See logs from a container and follow showing:
	docker logs -f <container_name>
## Run image:
	docker run <image_name>
## Run image with custom name:
	docker run --name test <image_name>
## Run and delete image:
	docker run --rm
## Run in interactive mode:
	docker run -it <image_name>
## Remove all containers:
	Powershell:
		docker ps -aq | foreach {docker rm $_}

## Remove all containers and images:
- ### Powershell:
		docker ps -aq | foreach {docker rmi $_}
- ### Windows bat:
		@echo off
		FOR /f "tokens=*" %%i IN ('docker ps -aq') DO docker stop %%i && docker rm %%i
		FOR /f "tokens=*" %%i IN ('docker images --format "{{.ID}}"') DO docker rmi %%i