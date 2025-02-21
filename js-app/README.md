# Containers with Docker 🐳

## Description

This demo project is part of Module 7: Containers with Docker from the Nana DevOps Bootcamp. It introduces the fundamentals of using Docker containers with MongoDB and Mongo-Express. The demo project covers:
- Setting up a Docker Network.
- Running MongoDB and Mongo-Express containers.
- Comparing the manual setup process with the Docker Compose YAML file approach. 

<br />


## 🚀 Technologies Used

- <b>Docker for containerization</b>
- <b>Mongo DB: Serves as a database to persist NodeJS data.</b>
- <b>Mongo-Express: WebUI access for managing Mongo DB.</b>
- <b>Linux: Ubuntu for Server configuration and management.</b>
- <b>NodeJs/npm: Nana's application from DevOps Bootcamp and package manager.</b>


## 🎯 Features

- <b>Create Mongo-Network in docker.</b>
- <b>Download and run MongoDB container.</b>
- <b>Download and run Mongo-Express container.</b>
- <b>Deploy NodeJs application.</b>
- <b>Runnning multiple docker containers with docker-compose.</b>

## 🏗 Project Architecture
<img src=""/>

## ⚙️ Project Configuration:
### Cloning Nana’s NodeJS Application Locally

To clone the NodeJS application from Nana DevOps Bootcamp, follow these steps:

1. Find the repository here: [Nana Bootcamp Repository]()
2. Clone the repository:
   ```bash
   git clone https://gitlab.com/twn-devops-bootcamp/latest/05-cloud/java-react-example

### Pulling Docker Images
The Docker images for this demo are available on [DockerHub](https://hub.docker.com/_/mongo)
1. Pull Image for MongoDB in this example I used the MongoDB:4.4 version as my machine was not compatible with MongoDB 5.

    ```bash
    docker pull mongo:4.4
    ```
2. Pull image for mongo-express.

    ```bash
    docker pull mongo-express
    ```
   
### Creating Mongo Network

1. Create a mongo-network using docker network create.
   
    ```bash
    docker create network mongo-network
    ```
    
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker/blob/main/Img/4.%20Create%20mongoNetwork.PNG"/>
    
### Running MongoDB Container
1. Run the MongoDB container using the docker run command.
   
   ```bash
   docker run \ #Docker Run command
   -d \ #Running Container in detach mode
   -p 27017:27017 \ #Mapping host:container ports
   -e MONGO_INITDB_ROOT_USERNAME= admin \ #Environment variable for MongoDB
   -e MONGO_INITDB_ROOT_PASSWORD= admin \ #Environment variable for MongoDB
   --name mongodb4 \ #Renaming the container
   --net mongo-network \ # Adding the container to mongo-network
   mongo:4.4 #Container Image
   
   ```
### Running Mongo-Express Container
1. Run the Mongo-Express container using the docker run command.

   ```bash
   docker run \ #Docker Run command
    -d \ #Running Container in detach mode
    -p 8081:8081 \ #Binding host:container ports
    -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \ #Environment variable for Mongo-Express
    -e ME_CONFIG_MONGODB_ADMINPASSWORD=admin \ #Environment variable for Mongo-Express
    -e ME_CONFIG_MONGODB_SERVER=mongodb4 \ #Environment variable for Mongo-Express
    --net mongo-network \ #Adding the container to mongo-network
    --name mongo-express \ #Renaming the container
    mongo-express #Container Image
   ```
### Access MongoDB with Browser
1. Open MongoDB using the browser and the mongo-express port:

   http://localhost:8081

   <img src=""/>

3. Create a New Database named user-account.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker/blob/main/Img/7%20Creating%20User%20account%20db.png"/>
   
4. Add a new collection named users to the user-account.

   <img src=""/>

### Deploy NodeJS application
1. Update the package manager to ensure it has the latest version.

    ```bash
   apt update
   ```

3. Navigate to the app directory and install dependencies with the npm install command.
   
   ```bash
   npm install
   ```
5. Run the application locally.

   ```bash
   node server.js &
   ```
6. Access the application from the browser

   http://localhost:3000/
   
8. Click on Edit profile and update the profile.

   <img src=""/>
   
10. Verify that the user has been updated in the User collection.

    <img src=""/>
    

### Running Multiple Containers with DOCKER-COMPOSE







## demo app - developing with Docker

This demo app shows a simple user profile app set up using 
- index.html with pure js and css styles
- nodejs backend with express module
- mongodb for data storage

All components are docker-based

### With Docker

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

Step 4: open mongo-express from browser

    http://localhost:8081

Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express

Step 6: Start your nodejs application locally - go to `app` directory of project 

    cd app
    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

### With Docker Compose

#### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: in mongo-express UI - create a new database "user-account"

Step 3: in mongo-express UI - create a new collection "users" in the database "user-account"       
    
Step 4: start node server 

    cd app
    npm install
    node server.js
    
Step 5: access the nodejs application from browser 

    http://localhost:3000

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.
