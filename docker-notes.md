# Docker Cheat Sheets

- [CLI Cheat Sheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [The Ultimate Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)
- [Docker Commands Cheat Sheet - PDF](https://phoenixnap.com/kb/wp-content/uploads/2022/12/docker-commands-cheat-sheet-pdf.pdf)
- [Docker Commands Cheat Sheet - WEB](https://phoenixnap.com/kb/docker-commands-cheat-sheet)

# Docker

[Docker](https://www.docker.com/) is a set of the platform as a service product that uses OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files and they can communicate with each other through well-defined channels. **Build - Share - Run**.

> Docker takes away repetitive, mundane configuration tasks and is used throughout the development lifecycle for fast, easy and portable application development – desktop and cloud. Docker’s comprehensive end to end platform includes UIs, CLIs, APIs and security that are engineered to work together across the entire application delivery lifecycle.

[Docker Compose](https://docs.docker.com/compose/) is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

## Building a Docker image, a.k.a Dockerizing with Dockerfiles

[Dockerfile](https://docs.docker.com/engine/reference/builder/) is a text file that contains instructions to build a Docker image. The images you create using a Dockerfile are then used to run a Docker container. Alternatively, you can pull images from the [Docker registry](https://hub.docker.com/) and build a container.

A Dockerfile contains commands such as:

| Command | Description |
| --- | --- |
| FROM | runs the base image of your application. If you are running an application that requires Node.js, you need to run Node.js as the base image on top of your application. |
| WORKDIR | creates a working directory within your application image. |
| COPY | a copy command that gest files and folders from your local computer to Docker. It copies these files to the working directory you create using the WORKDIR command. |
| RUN | execute commands that build your application. For example, when using Node.js, you install packages using npm install. Such commands are executed with RUN when using Docker. |
| EXPOSE | takes the port number parameter that sets the port number your application will be exposed to with the Docker image. |
| CMD | it executes commands for starting your application. For example, npm start. |

**Example**: writing the Node.js API Dockerfile

```
# We are using latest node version
FROM node:latest

# Add a work directory
WORKDIR /api

# Cache and install dependencies
COPY package*.json .
RUN npm install

# Copy app files
COPY . .

# Expose port
EXPOSE 5000

# Start app
CMD ["npm", "start"]
```

### Building the custom image

 Docker image can be created by using the following command in the root directory of the project.
 
 ```
 docker build -t my-docker-image .
 ```

### Docker and images, useful commands

To view all Docker images on the machine use the following command.

```
docker images -a 
```

To delete Docker images, issue the following command.

```
docker rmi image_name
```

## Running a container

If the image build is successful and there are no errors within the code, a container can be initialised using it. Execute the following command.

```
docker run -d --name my-container -p 5000:5000 my-docker-image
```

To view all containers that are running and also those that have stopped issue:

```
docker ps -a
```

## Stopping and deleting a container

To stop a container, issue the following command.

```
docker stop my-container
```

To delete a container, issue the following command.

```
docker rm my-container
```

# Docker compose

Instead of executing a 'docker run' command for each container that needs to be initialised, a 'docker-compose.yml' file can be used to create multiple containers. The Docker Compose documentation can be found [here](https://docs.docker.com/compose/).

**Example**: Setting up MySQL on Docker-compose

```
version: '3.8'
services:
  mysql_srv:
    image: mysql:8.0
    container_name: mysql_ctr
    stdin_open: true
    restart: always
    environment:
      MYSQL_DATABASE: <db-name>
      MYSQL_ROOT_PASSWORD: <db-password>
    ports:
      - "3307:3306"
    volumes:
      - ./data:/var/lib/mysql
      - ./conf:/etc/mysql/conf.d
      - ./logs:/logs
```

Once the 'docker-compose.yml' file is created and all services are configured as required, the following command can be used to launch all containers:

```
docker-compose up -d
```

The '-d' tag is used to run all the containers in the detached mode, meaning in the background.

The containers can be terminated by using the command:

```
docker-compose down
```
