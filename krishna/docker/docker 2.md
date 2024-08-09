
[[docker ultimate]]
# Actionable docker

Using docker to run packages locally.

Docker let’s you do a lot of things, here’s my tutorial on the same -

![Video preview](https://i.ytimg.com/vi/KuCwrySinqI/hqdefault.jpg)

![Video preview](https://i.ytimg.com/vi/fSmLiOMp2qI/hqdefault.jpg)

This tutorial is on `actionable docker` to start `packages` locally.

# Installing Docker

`Docker GUI` is the easiest way to get off the ground.

You can find instructions to install docker on [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

At the end of the installation, you need to make sure you’re able to run the following command -

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F7fbdc4db-9034-4ed6-a853-5ed4467cbf37%2FScreenshot_2024-02-20_at_10.47.51_AM.png?table=block&id=10f2b90f-3c6a-46f0-bc19-439b7d50a729&cache=v2)


# What are we using docker for?

Docker let’s you do a lot of things.

It let’s you `containerise` your applications.

It let’s you run other people’s `code + packages` in your machine.

It let’s you run common software packages inside a `container` (For eg - Mongo, Postgres etc)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F05156dd4-bd11-4143-a138-eee45e22e8fe%2FScreenshot_2024-02-20_at_10.57.18_AM.png?table=block&id=3be84b8f-fa14-45d1-b59c-85302cb3647e&cache=v2)


# Where can we get packages from?

Just like you can push your `code` to Github/Gitlab.

You can push `images` to `docker registries`

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F5da9bacc-13d0-4461-a847-c4ca38ceb939%2FScreenshot_2024-02-21_at_10.34.55_AM.png?table=block&id=d4e2900d-b6f8-491e-b89d-04d57581f47e&cache=v2)


# Common commands to know

1. docker run

2. docker ps

3. docker kill

### Running an image

#### 1. Running a simple image

Let’s say you wan’t to run MongoDB locally [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)

```javascript
docker run mongo
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fff31786a-fe9a-4c52-a14b-c1af65157769%2FScreenshot_2024-02-21_at_10.37.07_AM.png?table=block&id=c06d5bde-c3c4-4fc6-865a-c0403f538d23&cache=v2)

You will notice you can’t open it in `MongoDB Compass` .

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F80528531-81d4-4447-91fb-cd39313f4835%2FScreenshot_2024-02-21_at_10.38.43_AM.png?table=block&id=e92e39a4-51e4-4208-ae6f-a21860e1b6af&cache=v2)

#### Adding a port mapping

The reason is that you haven’t added a `port mapping`

```javascript
docker run  -p 27017:27017 mongo
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F4601c1cd-5b4c-41c9-826b-93f33f9d4f7f%2FScreenshot_2024-02-21_at_10.41.02_AM.png?table=block&id=5f8e22c8-f13b-46df-ac13-255708e0f54a&cache=v2)

#### Starting in detached mode

Adding `-d` will ensure it starts in the background

```javascript
docker run -d -p 27017:27017 mongo
```

### Inspecting a container

```javascript
docker ps
```

This will show you all the containers you are running.

### Stopping a container

```javascript
docker kill <container_id>
```

Will stop the container that you are running

In the end, this is the flow of commands -

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F2c747f8e-458e-4500-bbbf-4cf7ee7acf40%2FScreenshot_2024-02-21_at_10.43.18_AM.png?table=block&id=ac6834b0-fbab-4d50-ab3e-73093b99d662&cache=v2)


# Common packages

### Mongo

```javascript
docker run -d -p 27017:27017 mongo
```

### Postgres

```javascript
docker run -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 postgres
```

The connection string for this postgres would be

```javascript
postgresql://postgres:mysecretpassword@localhost:5432/postgres
```

Code to test it out

```javascript
// Import the pg library
const { Client } = require('pg');

// Define your connection string (replace placeholders with your actual data)
const connectionString = 'postgresql://postgres:mysecretpassword@localhost:5432/postgres';

// Create a new client instance with the connection string
const client = new Client({
  connectionString: connectionString
});

// Connect to the database
client.connect(err => {
  if (err) {
    console.error('connection error', err.stack);
  } else {
    console.log('connected to the database');
  }
});

// Run a simple query (Example: Fetching the current date and time from PostgreSQL)
client.query('SELECT NOW()', (err, res) => {
  if (err) {
    console.error(err);
  } else {
    console.log(res.rows[0]);
  }

  // Close the connection
  client.end();
});
```