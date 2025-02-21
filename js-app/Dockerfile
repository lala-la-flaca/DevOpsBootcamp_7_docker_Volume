FROM node:20-alpine

ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=admin

#creating /home/app directory in docker
RUN mkdir -p /home/node-app

#copying only the content from app folder to the home/app in docker
COPY ./app /home/node-app

# set default dir so that next commands executes in /home/app dir
WORKDIR /home/node-app

# will execute npm install in /home/app because of WORKDIR
RUN npm install

# no need for /home/app/server.js because of WORKDIR
CMD ["node", "server.js"]
