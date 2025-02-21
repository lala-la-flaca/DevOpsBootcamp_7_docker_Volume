# 🐳 Persisting Data with Docker Volumes
This demo project is part of Module 7: Containers with Docker from the Nana DevOps Bootcamp. It focuses on using Docker Volumes to persist data in a MongoDB container, ensuring that the database data is retained even after restarting the container.

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
    
    <img src="" width=500 />
    
2. Add the volume to the service. In this example, attach it to the MongoDB service.
    ```bash
      volumes:
      - mongo-data:/data/db
    ```
   ⚠️ **Note:**
   * Each database type stores its data in a different path. For MongoDB, the path is:
   ```bash
   /data/db
   ```
   
   <img src="" width=500 />
   
3. Access Mongo-Express, create a database named user-account, and add a collection called users.
   
   <img src="" width=500 />
   
4. Go to the application and update the user profile.
   
   <img src="" width=500 />
   
5. Restart the containers.
   
   <img src="" width=500 />
   
6. Verify that the data has persisted.
    
   <img src="" width=500 />
    
