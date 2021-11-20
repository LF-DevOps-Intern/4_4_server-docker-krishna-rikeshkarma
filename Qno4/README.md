# Now push the created docker images to the docker hub repository.

- To push the created docker images to the docker hub repository:
  - First login to the docker hub in cli using the following command:
    - `sudo docker login`
    - Fill your credentials and login.<br/>
  ![dockerhub login cli]()
  - Now first let’s push our node js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_nodejs rikeshkarma/qno3_nodejs`<br/>
  ![push nodejs to dockerhub]()
      - `sudo docker push rikeshkarma/qno3_nodejs`<br/>
  ![nodejs app on docker hub]()
  - Now first let’s push our react js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_reactjs rikeshkarma/qno3_reactjs`
      - `sudo docker push rikeshkarma/qno3_reactjs`<br/>
  ![push reactjs to docker hub]()<br/>
  ![reactjs app on docker hub]()
  - Now first let’s push our node js image to docker hub repository by using the following command:
    - Before we push we need to tag the locally created image to the docket hub, which means we need to tag the image with the docker hub username using the following command:
      - `docker tag qno3_nginx rikeshkarma/qno3_nginx`<br/>
  ![nginx to docker hub]()
      - `sudo docker push rikeshkarma/qno3_nginx`<br/>
  ![nginx on docker hub]()
