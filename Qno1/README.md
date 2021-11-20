# Install docker and then create a container (nginx) with docker cli (volume, network, port).

- Docker is an open source containerization platform. It enables developers to package applications into containers—standardized executable components combining application source code with the operating system (OS) libraries and dependencies required to run that code in any environment. Containers simplify delivery of distributed applications, and have become increasingly popular as organizations shift to cloud-native development and hybrid multi-cloud environments.<br/>
Developers can create containers without Docker, but the platform makes it
easier, simpler, and safer to build, deploy and manage containers. Docker is
essentially a toolkit that enables developers to build, deploy, run, update, and
stop containers using simple commands and work-saving automation through a
single API.
- To install docker we will be using the convenience script.
  - Let’s invoke the following commands one after another:
    - `curl -fsSL https://get.docker.com -o get-docker.sh`
    - `DRY_RUN=1 sh ./get-docker.sh`
      - ‘DRY_RUN=1’ is optional, we can use it if we want to learn what steps the script will execute during installation.<br/>
  ![installing docker](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno1/snapshots/installing%20docker.png)
  - Now we can very our installation by using the following command:
    - `docker version`<br/>
  ![verify docker installation](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno1/snapshots/verify%20docker%20installation.png)
    - After we verify docker installation, let’s add a docker group, add our current user to the docker group and switch the session to the docker group running the following commands:
      - `sudo groupadd docker`
      - `sudo usermod -aG docker $USER`
      - `newgrp - docker`<br/>
  ![group docker](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno1/snapshots/group%20docker.png)
- Now to create an Nginx container we need to run the command below in the terminal:
  - `docker container run -d --name nginx_container -v /home/rikeshkarma/docker/index:usr/share/nginx/html --network bridge -p 123:80 nginx`
    - **-d:-** This option is used to run the container in the detached mode.
    - **--name:-** This option is used to provide the name to the container, in our case, nginx_container is the name we have provided to our container. If we don’t use this option, the docker will assign the random alphanumeric string to the container.
    - **v:-** This option is used to mount the volume from the host to the container.
    - **network:-** This option will help to choose a network or we can create a new network too.
    - **p:-** This option will help to assign port from host to container (host:container)
    - **nginix:-** This is the name of the Nginx image.
  - We can list the containers and see the Nginx should be up and running. We can run the following command to see the list of containers:
    - `docker container ls -a`<br/>
  ![create nginx container](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno1/snapshots/create%20nginx%20container.png)
    - We can see that the Nginx server is running with default port **80** which is actually configured in the Nginx image Dockerfile. If we want to access the Nginx server, we must know the IP address of the Nginx server too. And in docker, each container has its own host and IP.
    - We can run the following command to display the properties of the container and file out the IP address.
      - `docker container inspect nginx_container | grep IPAddress`
        - **inspect:-** This command is used to display information on one or more containers.
        - **grep IPAddress:-** This is not the docker command, however, this is Linux specific command to find out any word from the command’s output.<br/>
  ![inspect our nginx container](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno1/snapshots/inspect%20our%20nginx%20container.png)
      - From the above command and the snapshot, we can see the result. And we can observe that the container’s IP is **172.17.0.2.**
