### Docker Commands
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

note: when a container is restarted the data inside the container would be gone 

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