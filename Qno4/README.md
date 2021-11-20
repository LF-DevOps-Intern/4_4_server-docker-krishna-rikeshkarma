# Now push the created docker images to the docker hub repository.

- To push the created docker images to the docker hub repository:
  - First login to the docker hub in cli using the following command:
    - `sudo docker login`
    - Fill your credentials and login.<br/>
  ![dockerhub login cli](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/dockerhub%20login%20cli.png)
  - Now first let’s push our node js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_nodejs rikeshkarma/qno3_nodejs`<br/>
  ![push nodejs to dockerhub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/push%20nodejs%20to%20docker%20hub.png)
      - `sudo docker push rikeshkarma/qno3_nodejs`<br/>
  ![nodejs app on docker hub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/nodejs%20app%20on%20docker%20hub.png)
  - Now first let’s push our react js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_reactjs rikeshkarma/qno3_reactjs`
      - `sudo docker push rikeshkarma/qno3_reactjs`<br/>
  ![push reactjs to docker hub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/push%20reactjs%20to%20docker%20hub.png)<br/>
  ![reactjs app on docker hub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/reactjs%20app%20on%20docker%20hub.png)
  - Now first let’s push our node js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_nginx rikeshkarma/qno3_nginx`<br/>
  ![nginx to docker hub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/nginx%20to%20docker%20hub.png)
      - `sudo docker push rikeshkarma/qno3_nginx`<br/>
  ![nginx on docker hub](https://github.com/LF-DevOps-Intern/4_4_server-docker-krishna-rikeshkarma/blob/main/Qno4/snapshots/nginx%20on%20docker%20hub.png)
