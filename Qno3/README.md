# Create a Dockerfile for nodejs, react and nginx and also create a container with docker compose file and mapped the port and volume in the same network.

- To create a Dockerfile for node js:
  - Firstly I created a simpler Node.js project using the following commands:
    - To initialize the project:
      - `npm init -y`
    - To install express.js
      - `npm install express`
    - Then I create a file named “index.js” and write this code:<br/>
  ![index js](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/index%20js.png)
    - Then we can run the following command to test if it works:
      - `node index.js`
  - Now after knowing our project is running file. Let’s create a Dockerfile,
    - Lets create a file named _“Dockerfile”_ in the project directory.
    - Then write this code inside the Dockerfile:<br/>
  ![nodejs dockerfile](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nodejs%20dockerfile.png)
    - We can also create _.dockerignore_ if we want to which will ignore the files/ directory we don't want ot push to docker hub. This file works like _.gitignore_.<br/>
  ![nodejs gitignore](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nodejs%20dockerfile.png)
- To create a Dockerfile for reactjs:
  - As I have already installed create-react-app for previous assignment, I can skip the installation part here.
  - Now let’s create a new React application using the following command:
    - `create-react-app reactjs`
    - Then cd into the reactjs directory and run to following command to check if its working fine:
      - `cd reactjs`
      - `npm start`
  - Now as our reactjs app is working fine. Let’s create a Dockerfile for this app same as we did for nodejs:
    - Lets create a file named _“Dockerfile”_ in the project directory.
    - Then write this code inside the Dockerfile:<br/>
  ![reactjs dockerfile](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/reactjs%20dockerfile.png)
    - We can also create _.dockerignore_ if we want to which will ignore the files/ directory we don't want ot push to docker hub. This file works like ._gitignore_.<br/>
  ![reactjs gitignore](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/reactjs%20dockerignore.png)
- To create a Dockerfile for Nginx:
  - For this let’s create a directory with name _“nginx”_ and inside the directory, let’s create a simple HTML file named “index.html”.This is our home page when we access the Nginx webserver. Let’s write this simple code inside the index.html file.<br/>
  ![nginx landing page](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nginx%20landingpage.png)
  - Now let’s create a Dockerfile for Nginx like we have did before:<br/>
  ![nginx dockerfile](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nginx%20dockerfile.png)
- After we are done creating Dockerfiles for all the services. Let’s now create a _docker-compose.yml_ file to combine all three created Dockerfiles.
  - At the root of this task, lets create a _docker-compose.yml_ file.<br/>
  ![docker compose file](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/docker%20compose%20file.png)
- After creating the docker compose file, now lets create a network so that all the the services will be mapped to the same port using the following command:
  - `sudo docker network create same`
- Now let’s build the docker image by running this command from the root folder:
  - `sudo docker-compose up -d`<br/>
  ![docker compose up](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/docker%20compose%20up.png)
- Now after the completion of the process. We can check to see if the containers are running:<br/>
  ![docker container ls](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/docker%20container%20ls.png)
- As we can observer all three services are running, we can browse them on the ports to see if all three services are running.
  - NodeJS<br/>
  ![nodejs on browser](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nodejs%20on%20browser.png)
  - ReactJS<br/>
  ![reactjs on browser](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/reactjs%20on%20browser.png)
  - Nginix<br/>
  ![nginx on browser](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno3/snapshots/nginx%20on%20browser.png)
