# Create a docker container with docker-compose file for mysql8 and also volume mount and port.

- Firstly let’s get Docker Compose on our system by running following commands sequentially:
  - `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
  - `sudo chmod +x /usr/local/bin/docker-compose`
  
- We can test if our installation was setup correctly by running:
  - `docker-compose --version`<br/>
  ![install docker compose]()
- Now we can create a file called _docker-compose.yml_. This file is essentially an instructions sheet for Docker where we tell docker what to do while creating the container. We write the following lines of code on the _docker-compose.yml_ file as on the snapshot below:<br/>
  ![docker compose file]()
- Now after this we can start our container by running the following command in the terminal inside the directory where we created our _docker-compose.yml_ file.
  - `docker-compose up`<br/>
  ![docker-compose up]()<br/>
  ![docker-compose up2]()
- We have created a container with a docker-compose file for mysql8. We can observe that the MySQL instance is running on **localhost:3306**.
