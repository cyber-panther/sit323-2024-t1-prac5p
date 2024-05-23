# Step-by-Step Documentation

#### Step 1: Installed Docker
- Downloaded Docker from the official [Docker website](https://www.docker.com/get-started) and installed it on the local machine.

#### Step 2: Cloned the Sample Web Application
- Used Git to clone the sample web application repository from GitHub.
  ```sh
  git clone https://github.com/agrimgautam/sit323-2024-t1-prac5p.git
  cd sit323-2024-t1-prac5p
  ```

#### Step 3: Created a Dockerfile
- Created a `Dockerfile` in the root directory of the project. The Dockerfile included instructions to use the Node.js base image, set the working directory, copy necessary files, install dependencies, expose the application port, and define the command to run the application.
  ```dockerfile
    # Use the official Node.js image as the base image
    FROM node:18.20.2

    # Set the working directory in the container
    WORKDIR /

    # Copy package.json and package-lock.json to the working directory
    COPY package*.json ./

    # Install dependencies
    RUN npm install

    # Copy the rest of the application code to the working directory
    COPY . .

    # Expose port 3000
    EXPOSE 3000

    # Command to run the application
    CMD ["node", "index.js"]
  ```

#### Step 4: Built the Docker Image
- Used the `docker build` command to build the Docker image from the Dockerfile.
  ```sh
  docker build -t agrimgautam/sit323-2024-t1-prac5p .
  ```

#### Step 5: Created a Docker Compose File
- Created a `docker-compose.yml` file in the project directory to define the services for the application.
  ```yaml
    version: '3'
    services:
    web:
        build: .
        ports:
          - "3000:3000"
  ```

#### Step 6: Started the Docker Compose Environment
- Started the application using Docker Compose with the `docker-compose up` command.
  ```sh
  docker-compose up
  ```

#### Step 7: Tested the Application
- Opened a web browser and navigated to `http://localhost:3000` to verify that the application was running correctly.

#### Step 8: Pushed the Docker Image to a Registry
- Logged into Docker Hub, tagged the Docker image, and pushed it to the Docker repository.
  ```sh
  docker login
  docker tag agrimgautam/sit323-2024-t1-prac5p agrimgautam/sit323-2024-t1-prac5p:latest
  docker push agrimgautam/sit323-2024-t1-prac5p:latest
  ```