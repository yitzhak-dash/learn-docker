# learn-docker

install packages
```
pip install -r requirements.txt
```
## docker terms:
`registry` is a collection of repositories

`repository` is a collection of images

`service` different pieces of the app

`docker-compose.yml` define, run, and scale services, You can name the Compose file anything you want to make it logically meaningful to you

`swarm` Multi-container, multi-machine applications are made possible by joining multiple machines into a “Dockerized” cluster called a swarm.
## docker commands:
creates a Docker image, which we’re going to tag using -t so it has a friendly name.
```
docker build -t friendlyhello .
```
```
docker images
```
run the app (mapping your machine’s port 4000 to the container’s published port 80)
```
docker run -p 4000:80 friendlyhello
```
run the app in the background, in detached mode:
Running the run command with the `-it` flags attaches us to an interactive tty in the container
```
docker run -d -p 4000:80 friendlyhello
```
```
docker container ls
```
stop container
```
docker stop <CONTAINER_ID>
```
login with id <453bace>
```
docker login
```
tag an image
```
docker tag <image> <username>/<repository>:<tag>
```
publish an image:
```
docker push username/repository:tag
```
docker image rm
```
docker image rm <image id>
```
 run your app on any machine:
```
docker run -p 4000:80 <username>/<repository>:<tag>
```
???
```commandline
docker swarm init
```
run service:(You have to give your app a name. Here, it is set to `getstartedlab`:)
```commandline
docker stack deploy -c docker-compose.yml getstartedlab
```
list services
```commandline
docker service ls
```
Docker swarms run tasks that spawn containers. Tasks have state and their own IDs:
```commandline
docker service ps <service>
```
list all containers:
```commandline
docker container ls -q
```
You can scale the app by changing the replicas value in docker-compose.yml, saving the change, and re-running the `docker stack deploy command`:
```commandline
docker stack deploy -c docker-compose.yml getstartedlab
```
Take the app down with docker stack rm:
```commandline
docker stack rm getstartedlab
```
Take down the swarm with :
```commandline
docker swarm leave --force
```
enable swarm mode and make your current machine a swarm manager
```commandline
docker swarm init
```
create VM:
```commandline
docker-machine create --driver virtualbox <machine_name>
```
show all running container
```commandline
docker ps
```