# Install docker swarm and manage the cluster of all created containers.

- Docker Swarm is a clustering tool that turns a group of Docker hosts into a single virtual server. Docker Swarm ensures availability and high performance for your application by distributing it over the number of Docker hosts inside a cluster. Docker Swarm also allows you to increase the number of container instance for
the same application.
- Docker swarm has already been installed automatically while we install the docker engine, so we don't need to do it manually. Now we just need to initialize it, for initializing we can invoke the following command:
  - `sudo docker swarm init --advertise-addr <host-ip>`
  - After using this command the docker swarm should be initialized.
  - Let’s verify that in case using the following command:
    - `sudo docker system info | grep Swarm`<br/>
  ![initialize and verify docker swarm](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/initialize%20and%20verify%20docker%20swarm.png)
- Firstly we need to join the worker’s node in order to manage the clusters of all created containers, so let’s do it:
  - Initially we need to install Docker Engine in the worker node. So let’s run the command that we got when we used swarm init in the VM so as to add a worker in the swarm. The command generated was:
    - `docker swarm join --token SWMTKN-1-1j2rc3fo5uiizg9g67m14u5zyj9w6056wp9fkp7cnkyn6asyq2-1yqvdt58dbcv3vhq9ikz6ig92 192.168.254.141:2377`<br/>
  ![node added as worker](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/node%20added%20as%20worker.png)
  - Now we can see that the node has been added to swarn as a worker, if we view the Docker info in manager mode using the following command:
    - `sudo docker info`<br/>
  ![docker swarm info](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/docker%20swarm%20info.png)
    - We can see that now there are **2 nodes**.
  - We can check the information about the nodes using the following command:
    - `sudo docker node ls`<br/>
  ![node info](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/node%20info.png)
    - We can see that there is a VM as a node as well. We can also see that our host machine is leader and the VM is worker (empty MANAGER STATUS) also both are active.
- Swarm services use a declarative model, which means that you define the desired state of the service, and rely upon Docker to maintain this state.
- Now lets create a swarm service using the following command:
  - `sudo docker service create --name nginx-service --mode global -d -p 80:80 nginx`
    - **--mode:-** This option will help to create the container in our desired mode. As our mode for this command is global, which means two containers will be created on the 2 nodes we have i.e manager node and worker node.
- After creating the service we can check the services and list the containers running by invoking the following commands:
  - `sudo docker service ls`
  - `sudo docker container ls`<br/>
  ![create swarm service and check](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/create%20swarm%20service%20and%20check.png)
- Now we can deploy the _docker-compose.yml_ to the worker node with custom build images we need to invoke the following commands:
  - But before that we need to make some changes in the _docker-compose.yml_ file. The snapshot of yml file after making the modifications is below and the file also available in the task repo:
  - Added modifications in the _docker-compose.yml_ files are:
    - **image:-** links to the previously pushed docker image. (dockerhubID/image-name)
    - **networks:-** changes has been name on the restart policy, stacking the network and replicas has been added to all theree services. Also mapping ports of all services driver has been added as overlay.<br/>
  ![edited docker-compose yml file](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/edited%20docker-compose%20yml%20file.png)
- We assign the service to run containers in the choice of our node by change this on the _docker-compose.yml_ file: (following to run on the manager mode)
  - deploy:
      placement:
        constraints:
          -node.role == manager
- Now lets deploy to the worker node i.e in the VM.
  - First we need to push the compose file to the Docker hub.
    - For this lets navigate to the directory where the docker-compose.yml file is located.
    - Then run the following command in the terminal:
    - `sudo docker-compose push`
  - Now to deploy stack with composer file use the following command:
    - `sudo docker stack deploy --compose-file docker-compose.yml qno5`<br/>
  ![deploy stack with composer file](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/deploy%20stact%20with%20composer%20file.png)
  - We can now check the details of the stack we just deployed using the following command:
    - `sudo docker stack ps qno5`<br/>
  ![view stack details](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/view%20stack%20details.png)
    - We can observe that qno5_reactjs container has been deployed to the worker node i.e in the VM.
  - We can now check on the VM as well for the containers, it must show the reactjs container created.
    - We can use the following command to verify:
      - `sudo docker container ls`
  - If we need we can also scale containers using the service from manager node to the worker node. For this we need to invoke this command:
    - `sudo docker service scale _<network-name>=num_
      - In our case we will use this command:
        - `sudo docker service scale qno5_nginx=2`<br/>
  ![scaling container](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/scaling%20container.png)
  - Let’s check on the VM i.e worker-node for the running containers again using this command:
    - `sudo docker container ls`<br/>
  ![checking worker node for running container](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno5/snapshots/checking%20worker%20node%20for%20running%20container.png)
    - Here the container with my react js is not showing because just before this my VM crashed while taking the screenshot for the previous ls command to show reactjs running on worker node and I tried to review the previous processes but due to some issue its not showing, my apologies.
