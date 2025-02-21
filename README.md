# 🐳 Persisting Data with Docker Volumes
This demo project is part of Module 7: Containers with Docker from the Nana DevOps Bootcamp. It focuses on using Docker Volumes to persist data in a MongoDB container, ensuring that the database data is retained even after restarting containers.

## 🚀 Technologies Used

- <b>Docker for containerization.</b>
- <b>Mongo DB: Serves as a database.</b>
- <b>Mongo-Express: WebUI access for managing Mongo DB.</b>
- <b>Linux: Ubuntu for Server configuration and management.</b>
- <b>NodeJs/npm: Nana's application from DevOps Bootcamp and package manager.</b>
- <b>Docker Volumes: Serves to persist data from MongoDB.</b>


## 🎯 Features

- <b>Docker Volume Integration.</b>

## 🏗 Project Architecture

<img src=""/>


## ⚙️ Project Configuration:

### Adding a Docker Volume
1. Add the volume to the docker YAML file by specifying its name and driver.
    ```bash
    volumes:
      mongo-data:
        driver: local
    ```
    
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/DefiningVolumeDockerComposeFile.png" width=800 />
    
2. Add the volume to the service. In this example, attach the volume to the MongoDB service.
    ```bash
      volumes:
      - mongo-data:/data/db
    ```
   ⚠️ **Note:**
   * Each database type stores its data in a different path. For MongoDB, the path is:
   ```bash
   /data/db
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/AddingTheVolumetoService.png" width=800 />
   
3. Run the NodeJS application
   ```bash
    npm install
    node server.js
   ```

4. Run docker-compose command to run the containers.

   ```bash
   docker compose -f docker-compose.yaml up
   ```
   
5. Access Mongo-Express, create a database named user-account, and add a collection called users.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/CreatingDatabaseandCollection.png" width=800 />
   
6. Go to the application and update the user profile.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/UdatinUserinApp.png" width=800 />
   
7. Restart the containers.
   
   ```bash
   docker compose -f docker-compose.yaml down
   docker compose -f docker-compose.yaml up
   
   ```
      
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/RestartingContainers.png" width=800 />
   
8. Verify that the data has persisted.
    
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Volume/blob/main/Img/DataPersisted.png" width=800 />
    
