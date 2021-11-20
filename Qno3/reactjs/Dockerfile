# pull the official base image
FROM node:alpine
# set working direction
WORKDIR /app
# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH
# copy the packages and add app
COPY package*.json . ./
# install application dependencies
RUN npm install
# expose the port
EXPOSE 4000
# start app
CMD ["node", "start"]