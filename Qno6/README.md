# Install the portainer and manage the docker from GUI. Practice the features and attach the snapshots.

- Portainer is a Web User Interface (WUI/GUI) dashboard tool, which can be used to monitor and centrally manage a docker platform. With Portainer, We can add/login to a registry, Manage multiple hosts, Manage hosts on different networks, Build a Container (Docker) Image, pull and push an image from/to container registry, Manage running/deployed containers, deploy a stack/container, Manage accounts, and many more. Other than standalone docker platform, Portainer also supports Docker Swarm and Kubernetes cluster. Above that, All of them can be managed from single centrally managed dashboard UI.
- Now let’s start by installing portainer first:
  - The installation requires root access for proper functioning on the dashboard so let’s invoke this command first:
    - `sudo su`
  - Let’s create a docker volume for portainer data by using this command:
    - `docker volume create portainer_data`
  - Now let’s deploy portainer server on our local machine using this command:
    - `docker run --detach --name portainer --publish 9443:9443 --volume /var/run/docker.sock:/var/run/docker.sock --volumeportainer_data:/data --restart=always portainer/portainer-ce:2.9.0-alpine`<br/>
  ![deploying portainer server]()
  - Now Port 9443 can be used for web UI access. Docker socket is required to be mounted on Portainer container to allow it to access docker daemon.
  - We can check if portainer is up and running or not by invoking the following command:
    - `docker ps`<br/>
  ![checking portainer server]()
    - We can observer that portainer server is up and running with CONTAINER ID c6116c05ae3d.
  - Now let’s check on our browser at _https://localhost:9443_.<br/>
  ![portainer on browser]()
  - Let’s setup the admin credentials first. Then we can see our dashboard with all our local services, containers, images, volumes, networks and others.<br/>
  ![portainer dashboard]()
  - We can find alot of features here. Let’s practice some of the features:
    - Build a container/ docker image
      - Image -> Build a new image<br/>
  ![build a new image]()
      - In image section, we can see all the list of the pulled images in the environment. We can also see **Build a new image** button. We can click on it and we can see that we can write a Dockerfile in the webeditor or upload a tarball or use an URL to build an image. Let’s build a sample nginx:test image,<br/>
  ![building image in portainer]()
      - We can see this working in the snapshot below:<br/>
  ![output after building image in portainer]()
    - Pull an image from registry
      - Let’s click on images from the left panel and choose registry from the drop down list. We need to add image name with tag and then pull the image:<br/>
  ![pull the image from registry]()
    - Run commands inside container (Exec inside container)
      - Now let’s select containers from the left panel and choose any running container. Then we can click on the console as in the snapshot below:<br/>
  ![select running container and console click]()
      - After that we can give it with a custom command or use shell binary present in container.<br/>
  ![custom command]()
    - Monitor resource usage of a container
      - Like before open a container from a running container’s list.
      - Then click on stats to monitor resource usages of the particular container.<br/>
  ![container resource usage]()
    - Manage accounts
      - We can also set up custom authentication methods under settings and then click on authentication as on the snapshot below:
      - We can create and manage Roles, Teams and users from Settings and then Users Section. This can be used to grant access to other developers and cut off their duties.<br/>
  ![authentication settings]()