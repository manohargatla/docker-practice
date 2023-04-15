Day1
----
* Docker installation steps
    * To install docker firstly we have to create a linux machine.
    * Required commands for installation of docker
    * `sudo apt update`
    * `curl -fsSL https://get.docker.com -o get-docker.sh` && `sh get-docker.sh`
    * Add user into docker group by using below command
    * `sudo usermod -aG docker ubuntu`
    * Exit from the linux machine
    * Reconnect it 
    * type the command `docker info`
    * ![preview](images/docker1.png)
* DOCKER WORKBOOK – 1
 * RUNNING DOCKER CONTAINERS  
* Run hello-world docker container and observe the container status?
  * `docker container run -d -P --name myworld hello-world:latest`
  * `docker container run -it -P --name myworld hello-world:latest`
  * To see the container is running or not `docker container ls`
  * ![preview](images/docker2.png)
  * ![preview](images/docker3.png)
  * ![preview](images/docker4.png)
* Check the docker images and also write down the size of hello-world image?
  * ![preview](images/docker5.png)
* Run the nginx container with name as nginx1 and expose it on 8080 port on docker host?
  * ![preview](images/docker6.png)
  * ![preview](images/docker7.png)
* Explain docker container lifecycle?
  * The complete lifecycle of a docker container revolves around 
  * Phases: Create phase, Running phase, Paused phase/unpause phase, start phase, stop phase, remove phase of container.
  * ![preview](images/docker8.png)
* Explain what happens when you run the docker container?
  * The docker run command creates running containers from images and can run commands inside them.When using the docker run command, a container can run a default action (if it has one), a user specified action, or a shell to be used interactively.
* Show all the states of docker container on nginx based container?
  * ![preview](images/docker9.png)
* Explain docker architecture?
  * Docker architecture. Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon.
  * ![preview](images/docker10.png)

Day2
---
* Nodejs-Express application
  * commands to build and create.
  * To build image:"docker image build -t node1:16-alpine ." <name:version>
  * To Create container :"docker container run --name newjs -d -P 1a0288859300 =>"<image name/id>

 * trail-1
 * FROM node:16-alpine
 * LABEL author="Manu" organization="khaja.tec" project="nodejs"
 * RUN apk add --update npm && \
   * apk add git && \
   * git clone https://github.com/expressjs/express.git && \
   * cd express && \
   * npm install express && \
   * npm install -g express-generator@4 && \
   * express /tmp/foo && \
   * cd /tmp/foo && \
   * npm install
* WORKDIR /tmp/foo
* EXPOSE 3000
* CMD ["npm", "start"]

output :
![preview](images/docker12.png)

trail-2
FROM node:16-alpine
LABEL author="Manu" organization="khaja.tec" project="nodejs"
RUN apk add --update  && \
    apk add git && \
    git clone https://github.com/expressjs/express.git \
    && cd express && \
    npm install express && \
    npm install -g express-generator@4 && \
    express /tmp/foo && cd /tmp/foo && \
    npm install
WORKDIR /tmp/foo
EXPOSE 3000
CMD ["npm", "start"]


    