# Step 1 - Why Docker?

Docker/containers are important for a few reasons -

1. Kubernetes/Container orchestration

2. Running processes in isolated environments

3. Starting projects/auxilary services locally
# Step 2 - Containerization

#### What are containers

Containers are a way to package and distribute software applications in a way that makes them easy to deploy and run consistently across different environments. They allow you to package an application, along with all its dependencies and libraries, into a single unit that can be run on any machine with a container runtime, such as Docker.

#### Why containers

1. Everyone has different Operating systems

2. Steps to run a project can vary based on OS

3. Extremely harder to keep track of dependencies as project grows

#### Benefits of using containers

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F2775ef7f-d916-4397-bbd9-e8ce58eeddb6%2FScreenshot_2024-03-09_at_1.01.25_PM.png?table=block&id=22377015-a7ed-439d-9a51-717dba681af5&cache=v2)

1. Let you describe your `configuration` in a single file

2. Can run in isolated environments

3. Makes Local setup of OS projects a breeze

4. Makes installing auxiliary services/DBs easy

#### References

- For Reference, the following command starts `mongo` in all operating systems -

```javascript
docker run -d -p 27017:27017 mongo
```

- Docker isn’t the only way to create containers

# step 3 - History of Docker


Docker is a YC backed company, started in ~2014

They envisioned a world where containers would become mainstream and people would deploy their applications using them

That is mostly true today

Most projects that you open on Github will/should have docker files in them (a way to create docker containers)

Ref - [https://www.ycombinator.com/blog/solomon-hykes-docker-dotcloud-interview/](https://www.ycombinator.com/blog/solomon-hykes-docker-dotcloud-interview/)


# Step 4 - Installing docker

[https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F47bccdb7-296f-44d4-abce-116390d8331a%2FScreenshot_2024-03-09_at_1.19.12_PM.png?table=block&id=f014bb98-5216-45c4-877f-0605fdba02d5&cache=v2)

Make sure you’re able to run the `docker cli` locally -

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F030c2f58-ac9d-4ab4-b6bf-87a3efbf4aac%2FScreenshot_2024-03-09_at_1.23.18_PM.png?table=block&id=5062c2b3-b72a-4e41-99a4-81116929d142&cache=v2)


# Step 5 - Inside docker

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Ff09be77f-3157-45a8-98db-f6109c8a0200%2FScreenshot_2024-03-09_at_2.08.40_PM.png?table=block&id=73f531cb-9909-488d-bcf1-00ef5373cb90&cache=v2)

As an application/full stack developer, you need to be comfortable with the following terminologies -

1. Docker Engine

2. Docker CLI - Command line interface

3. Docker registry

### 1. Docker Engine

Docker Engine is an open-source `containerization` technology that allows developers to package applications into `container`

Containers are standardized executable components combining application source code with the operating system (OS) libraries and dependencies required to run that code in any environment.

### 2. Docker CLI

The command line interface lets you talk to the `docker engine` and lets you start/stop/list containers

```javascript
docker run -d -p 27017:27017 mongo
```

💡

Docker cli is not the only way to talk to a docker engine. You can hit the docker `REST` API to do the same things

### 3. Docker registry

The `docker registry` is how Docker makes money.

It is similar to `github`, but it lets you push `images` rather than `sourcecode`

Docker’s main registry - [https://dockerhub.com/](https://dockerhub.com/)

Mongo image on docker registry - [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)

# Step 6 - Images vs containers

**Docker Image**

A Docker image is a lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.

💡

A good mental model for an image is `Your codebase on github`

**Docker Container**

A container is a running instance of an image. It encapsulates the application or service and its dependencies, running in an isolated environment.

💡

A good mental model for a container is when you run `node index.js` on your machine from some source code you got from github

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F29e64869-22c7-41ba-8697-ac4f2b4fd7c1%2FScreenshot_2024-03-09_at_2.25.41_PM.png?table=block&id=e53e71d7-c961-4348-9552-c9c17d72b0eb&cache=v2)
# Step 7 - Port mapping

```javascript
docker run -d -p 27018:27017 mongo
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F08e0e5c3-2a5c-4049-8b23-f5c7a0a65e2d%2FScreenshot_2024-03-09_at_5.16.57_PM.png?table=block&id=9319a0cd-c86a-408e-8e88-8ddce950655b&cache=v2)

# Step 8 - Common docker commands

1. docker images

2. docker ps

3. docker run

4. docker build

### 1. docker images

Shows you all the images that you have on your machine

### 2. docker ps

Shows you all the containers you are running on your machine

### 3. docker run

Lets you start a container

1. -p ⇒ let’s you create a port mapping

2. -d. ⇒ Let’s you run it in detatched mode

### 4. docker build

Lets you build an image. We will see this after we understand how to create your own `Dockerfile`

### 5. docker push

Lets you push your image to a registry

### 6. Extra commands

1. docker kill

2. docker exec
# Step 9 - Dockerfile

### What is a Dockerfile

If you want to create an image from your own code, that you can push to `dockerhub`, you need to create a `Dockerfile` for your application.

A Dockerfile is a text document that contains all the commands a user could call on the command line to create an image.

### How to write a dockerfile

A dockerfile has 2 parts

1. Base image

2. Bunch of commands that you run on the base image (to install dependencies like Node.js)

### Let’s write our own Dockerfile

Let’s try to containerise this backend app - [https://github.com/100xdevs-cohort-2/week-15-live-1](https://github.com/100xdevs-cohort-2/week-15-live-1)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F6b0619fb-054b-4ba4-a82b-d7524c903bd8%2FScreenshot_2024-03-09_at_3.17.15_PM.png?table=block&id=47b44c7c-f5e1-44df-a90a-ee2e1b4bbbec&cache=v2)

Solution

```javascript
FROM node:20

WORKDIR /app

COPY . .

RUN npm install
RUN npx prisma generate
RUN npm run build

EXPOSE 3000

CMD ["node", "dist/index.js"]
```

### Common commands

- `**WORKDIR**`: Sets the working directory for any `**RUN**`, `**CMD**`, `**ENTRYPOINT**`, `**COPY**`instructions that follow it.

- `**RUN**`: Executes any commands in a new layer on top of the current image and commits the results.

- `**CMD**`: Provides defaults for executing a container. There can only be one CMD instruction in a Dockerfile.

- `**EXPOSE**`: Informs Docker that the container listens on the specified network ports at runtime.

- `**ENV**`: Sets the environment variable.

- `**COPY**`: Allow files from the Docker host to be added to the Docker image

[https://github.com/100xdevs-cohort-2/week-15-live-1](https://github.com/100xdevs-cohort-2/week-15-live-1)

# Step 10 - Building images

Now that you have a dockerfile in your project, try building a `docker image` from it

```javascript
docker build -t image_name .
```

Now if you try to look at your images, you should notice a new image created

```javascript
docker images
```

💡

Add a .dockerignore so that node_modules don’t get copied over
# Step 11 - Running images

```javascript
docker run -p 3000:3000 image_name
```

Try visiting `localhost:3000`

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F6a51c694-85c5-4072-bcb7-522a3f7b0314%2FScreenshot_2024-03-09_at_4.14.02_PM.png?table=block&id=5eeb0e92-2b81-4755-ab23-5ac1bdbdf70e&cache=v2)

# Step 12 - Passing in env variables

```javascript
docker run -p 3000:3000 -e DATABASE_URL="postgres://avnadmin:AVNS_EeDiMIdW-dNT4Ox9l1n@pg-35339ab4-harkirat-d1b9.a.aivencloud.com:25579/defaultdb?sslmode=require" image_name
```

The `-e` argument let’s you send in environment variables to your node.js app

# Step 13 - More commands

1. docker kill - to kill a container

2. docker exec - to exectue a command inside a container

Examples

1. List all contents of a container folder

```javascript
docker exec <container_name_or_id> ls /path/to/directory
```

1. ****Running an Interactive Shell****

```javascript
docker exec -it <container_name_or_id> /bin/bash
```


# Step 14 - Pushing to dockerhub

Once you’ve created your image, you can push it to `dockerhub` to share it with the world.

1. Signup to `dockerhub`

2. Create a new repository

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Ff28b0281-9aa7-4a45-8609-92953912dd2c%2FScreenshot_2024-03-09_at_4.40.21_PM.png?table=block&id=a393771d-6b3d-4c55-a053-fa526418bcf8&cache=v2)

3. Login to docker cli

1. docker login
2. you might have to create an access token - [https://docs.docker.com/security/for-developers/access-tokens/](https://docs.docker.com/security/for-developers/access-tokens/)

4. Push to the repository

```javascript
docker push your_username/your_reponame:tagname
```
# Step 15 - Layers in Docker

In Docker, layers are a fundamental part of the image architecture that allows Docker to be efficient, fast, and portable. A Docker image is essentially built up from a series of layers, each representing a set of differences from the previous layer.

**How layers are made -**

1. **Base Layer:** The starting point of an image, typically an operating system (OS) like Ubuntu, Alpine, or any other base image specified in a Dockerfile.

2. **Instruction Layers:** Each command in a Dockerfile creates a new layer in the image. These include instructions like `**RUN**`, `**COPY**`, which modify the filesystem by installing packages, copying files from the host to the container, or making other changes. Each of these modifications creates a new layer on top of the base layer.

3. **Reusable & Shareable:** Layers are cached and reusable across different images, which makes building and sharing images more efficient. If multiple images are built from the same base image or share common instructions, they can reuse the same layers, reducing storage space and speeding up image downloads and builds.

4. **Immutable:** Once a layer is created, it cannot be changed. If a change is made, Docker creates a new layer that captures the difference. This immutability is key to Docker's reliability and performance, as unchanged layers can be shared across images and containers.
# Step 16 - Layers practically

For a simple Node.js app - [https://github.com/100xdevs-cohort-2/week-15-live-2](https://github.com/100xdevs-cohort-2/week-15-live-2)

**Dockerfile**

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fa7018106-27d9-4833-9206-d20d05ab8a11%2FScreenshot_2024-03-10_at_1.29.42_PM.png?table=block&id=5adef147-fe82-4e9a-9e82-dbb3738b3104&cache=v2)

**Logs**

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F891e06cd-8ce7-402e-9e0d-15d7e9852e3d%2FScreenshot_2024-03-10_at_1.31.53_PM.png?table=block&id=d06687c2-32b3-4419-865c-367f7a0ffdd8&cache=v2)

#### Observations -

1. Base image creates the first layer

2. Each `RUN`, `COPY` , `WORKDIR` command creates a new layer

3. Layers can get re-used across docker builds (notice `CACHED` in 1/6)
# Step 17 - Why layers?

If you change your Dockerfile, layers can get re-used based on where the change was made

💡

If a layer changes, all subsequent layers also change

#### Case 1 - You change your source code

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F56478744-6865-470c-a271-1837d86bdf87%2FScreenshot_2024-03-10_at_1.38.04_PM.png?table=block&id=0ef9171c-dba1-4dd5-88bf-f7eade9b197d&cache=v2)

Logs

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fe394bcde-4a1e-4793-b990-ac300a217212%2FScreenshot_2024-03-10_at_1.41.27_PM.png?table=block&id=244d5b29-cb92-4ce2-81ad-e7ec0dbc2230&cache=v2)

#### Case 2 - You change the package.json file (added a dependency)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F56478744-6865-470c-a271-1837d86bdf87%2FScreenshot_2024-03-10_at_1.38.04_PM.png?table=block&id=70ac3431-e628-4238-b115-c724a55ffa5d&cache=v2)

Logs

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fe394bcde-4a1e-4793-b990-ac300a217212%2FScreenshot_2024-03-10_at_1.41.27_PM.png?table=block&id=3eae7431-5ea2-4f49-9c0a-46b9e88b2f78&cache=v2)

### Thought experiment

How often in a project do you think `dependencies change` ?

How often does the `npm install` layer need to change?

Wouldn’t it be nice if we could `cache` the `npm install` step considering dependencies don’t change often?
# Step 18 - Optimising Dockerfile

What if we change the Dockerfile a bit -

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F3dc112b6-bf1a-4d48-acd4-dcaac3ef594a%2FScreenshot_2024-03-10_at_2.24.00_PM.png?table=block&id=d3ab0f48-79e0-47c0-8370-5d9e18accb34&cache=v2)

Dockerfile

```javascript
FROM node:20

WORKDIR /usr/src/app

COPY package* .
COPY ./prisma .
    
RUN npm install
RUN npx prisma generate

COPY . .

EXPOSE 3000

CMD ["node", "dist/index.js", ]
```

1. We first copy over only the things that `npm install` and `npx prisma generate` need

2. Then we run these scripts

3. Then we copy over the rest of the source code

#### Case 1 - You change your source code (but nothing in package.json/prisma)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F60fd50e5-576a-4039-a0e0-6617293d10ce%2FScreenshot_2024-03-10_at_2.29.47_PM.png?table=block&id=e69f3527-8cd6-42a7-9d94-b17ac42467f0&cache=v2)

#### Case 2 - You change the package.json file (added a dependency)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fda3357b0-33e6-47ab-b552-4e52ecbfa808%2FScreenshot_2024-03-10_at_2.30.51_PM.png?table=block&id=c8cc1aaf-8c6a-48d4-b764-f1531207260b&cache=v2)


# Step 19 - Networks and volumes

Networks and volumes are concepts that become important when you have multiple containers running in which you

1. Need to persist data across docker restarts

2. Need to allow containers to talk to each other

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fbc784ebf-de6a-47ac-bb73-5fd44ba82e46%2FScreenshot_2024-03-10_at_3.28.40_PM.png?table=block&id=f4d28211-1790-4f26-85da-9e55cf259f89&cache=v2)

💡

We didn’t need `networks` until now because when we started the `mongo` container, it was being accessed by a Node.js process running directly on the machine

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fb39e85ed-9f88-4eac-aa94-9b5ab8399a2f%2FScreenshot_2024-03-10_at_3.28.01_PM.png?table=block&id=765feab2-fc70-440b-a7b3-b077a0c3fb4d&cache=v2)

# step 20 - Volumes

If you restart a `mongo` docker container, you will notice that your data goes away.

This is because docker containers are `transitory` (they don’t retain data across restarts)

## Without volumes

1. Start a mongo container locally

```javascript
docker run -p 27017:27017 -d mongo
```

1. Open it in MongoDB Compass and add some data to it

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F8c867185-969d-4d72-b3be-d3cb386903ef%2FScreenshot_2024-03-10_at_3.44.35_PM.png?table=block&id=a4a9ef50-3b92-488d-a365-2223c3e92b07&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fb8c8ef76-2b19-468f-8bed-2660f6c34496%2FScreenshot_2024-03-10_at_3.48.44_PM.png?table=block&id=b093a08e-119b-4fa0-b0db-9ad3c02bcaa2&cache=v2)

1. Kill the container

```javascript
docker kill <container_id>
```

1. Restart the container

```javascript
docker run -p 27017:27017 -d mongo
```

1. Try to explore the database in Compass and check if the data has persisted (it wouldn’t)

## With volumes

1. Create a `volume`

```javascript
docker volume create volume_database
```

1. Mount the folder in `mongo` which actually stores the data to this volume

```javascript
docker run -v volume_database:/data/db -p 27017:27017 mongo
```

1. Open it in MongoDB Compass and add some data to it

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F8c867185-969d-4d72-b3be-d3cb386903ef%2FScreenshot_2024-03-10_at_3.44.35_PM.png?table=block&id=cdf21e0d-100b-4091-b832-3d4a3887d7ab&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fb8c8ef76-2b19-468f-8bed-2660f6c34496%2FScreenshot_2024-03-10_at_3.48.44_PM.png?table=block&id=62467d68-6603-418d-abcf-db442078e6ce&cache=v2)

1. Kill the container

```javascript
docker kill <container_id>
```

1. Restart the container

```javascript
docker run -v volume_database:/data/db -p 27017:27017 mongo
```

1. Try to explore the database in Compass and check if the data has persisted (it will!)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F48644994-0923-4459-b39d-e82ffe5a2b22%2FScreenshot_2024-03-10_at_4.23.28_PM.png?table=block&id=ea7ea840-454b-4866-9412-0079d6769bf3&cache=v2)


# Step 21 - Network

In Docker, a network is a powerful feature that allows containers to communicate with each other and with the outside world.

Docker containers can’t talk to each other by default.

[`localhost`](http://localhost/) on a docker container means `it's own network` and not the network of the `host machine`

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F8b69d8c4-0014-46a6-80ee-b6fc40e07765%2FScreenshot_2024-03-10_at_4.32.34_PM.png?table=block&id=ad64379b-d26c-43ad-987b-628383216586&cache=v2)

### How to make containers talk to each other?

Attach them to the same network

1. Clone the repo - [https://github.com/100xdevs-cohort-2/week-15-live-2.2](https://github.com/100xdevs-cohort-2/week-15-live-2.2)

2. Build the image

```javascript
docker build -t image_tag .
```

1. Create a network

```javascript
docker network create my_custom_network
```

1. Start the `backend process` with the `network` attached to it

```javascript
docker run -d -p 3000:3000 --name backend --network my_custom_network image_tag
```

1. Start mongo on the same network

```javascript
docker run -d -v volume_database:/data/db --name mongo --network my_custom_network -p 27017:27017 mongo
```

1. Check the logs to ensure the db connection is successful

```javascript
docker logs <container_id>
```

1. Try to visit an endpoint and ensure you are able to talk to the database

2. If you want, you can remove the port mapping for mongo since you don’t necessarily need it exposed on your machine

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F2d10fe34-c5af-4030-bf82-09f6ecf2c545%2FScreenshot_2024-03-10_at_5.16.46_PM.png?table=block&id=0b77d3ea-2dbc-41ca-ba4e-d49172524991&cache=v2)

#### Types of networks

- **Bridge**: The default network driver for containers. When you run a container without specifying a network, it's attached to a bridge network. It provides a private internal network on the host machine, and containers on the same bridge network can communicate with each other.

- **Host**: Removes network isolation between the container and the Docker host, and uses the host's networking directly. This is useful for services that need to handle lots of traffic or need to expose many ports


# Step 22 - docker-compose

Docker Compose is a tool designed to help you define and run multi-container Docker applications. With Compose, you use a YAML file to configure your application's services, networks, and volumes. Then, with a single command, you can create and start all the services from your configuration.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F161f82ec-cbf1-4654-ab9b-a052fd1da6be%2FScreenshot_2024-03-10_at_5.36.58_PM.png?table=block&id=8e4f86ba-c720-4f78-8c97-1926391deb73&cache=v2)

### Before docker-compose

- Create a network

```javascript
docker network create my_custom_network
```

- Create a volume

```javascript
docker volume create volume_database
```

- Start mongo container

```javascript
docker run -d -v volume_database:/data/db --name mongo --network my_custom_network  mongo
```

- Start backend container

```javascript
docker run -d -p 3000:3000 --name backend --network my_custom_network backend
```

### After docker-compose

1. Install docker-compose - [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

2. Create a `yaml` file describing all your containers and volumes (by default all containers in a docker-compose run on the same network)

Solution

```javascript
version: '3.8'
services:
  mongodb:
    image: mongo
    container_name: mongodb
    ports:
      - "27017:27017"
    volumes:
      - mongodb_data:/data/db

  backend22:
    image: backend
    container_name: backend_app
    depends_on:
      - mongodb
    ports:
      - "3000:3000"
    environment:
      MONGO_URL: "mongodb://mongodb:27017"

volumes:
  mongodb_data:
```

1. Start the compose

```javascript
docker-compose up
```

1. Stop everything (including volumes)

```javascript
 docker-compose down --volumes
```
