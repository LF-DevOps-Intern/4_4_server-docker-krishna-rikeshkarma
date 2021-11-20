# pull the official base image
FROM node:alpine
# set working direction
WORKDIR /home/node/app
# copy the packages and add app
COPY package*.json index.js ./
# install application dependencies
RUN npm install
# expose the port
EXPOSE 3000
# start app
CMD ["node", "index.js"]