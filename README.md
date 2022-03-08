# Docker Commands
## Save:
 - docker save huzefa/test-app2 -o test-app2.tar

## run the container with streamlit defined port:
 - docker run -it --name my_container2 -p 8502:8502 -e STREAMLIT_SERVER_PORT=8502 huzefa/test-app2

## Build Image:
 - docker build -t huzefa/test-app2 .

## Remove image: 
 - docker rmi [imgid]

## show the list of containers
 -a to show containers that are stopped as well
 - docker ps -a 

## -d is to run docker container in demonize mode, in the background
 - docker run --name webserver -p 80:80 -d nginx

## To stop docker container
 - docker stop webserver

## remove container

 - docker rm webserver

## To run compose file:
 - docker-compose -f [file_name] up
 - docker-compose up --build
 - docker-compose down

note: when a container is restarted the data inside the container would be gone , for data persistance we can create volume
# Volume:
## Create Volume:
 - docker volume create --name DataVolume
## To verify:
 We can verify that the volume is present on our system with docker volume inspect
 - docker volume inspect DataVolume
## To remove:
 - docker volume rm DataVolume
## Create volume with container image for e.g (ubuntu):
 - docker run -dit -P --name ubuntu-test -v /DataVolume:/datavolume ubuntu

    The above command breaks down like this:

    - docker run is the main command that says we’re going to run a command in a new container.
    - -dit is d for detached mode, and it ensures that bash or sh can be allocated to a pseudo terminal, -t will give us a terminal and -i will allow us to interact with it
    - -P publishes the containers ports to the host.
    - --name says what follows is the name of the new container.
    - -v says what follows is to be the volume.
    - ubuntu is the image to be used for the container.
    
    **Note**: The -v flag is very flexible. It can bindmount or name a volume with just a slight adjustment in syntax. For example:
    - -v /path:/path/in/container mounts the host directory, /path at the /path/in/container
    - -v path:/path/in/container creates a volume named path with no relationship to the host.


# Portainer:
## create volume:
 - docker volume create portainer_data
## install portainer
 - docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
## volume for window:
 - -v \\.\pipe\docker_engine:\\.\pipe\docker_engine

## LINKS
 - https://github.com/docker/awesome-compose
 - https://docs.docker.com/engine/reference/builder/