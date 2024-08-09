
# Intro

Ref [https://docs.docker.com/engine/swarm/](https://docs.docker.com/engine/swarm/)

Docker swarm is a container orchestration system, very similar to kubernetes.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fe2bd9248-9ff7-4855-99fb-63afd52e7219%2FeJiZxESrQu-E-DNl7S3Nlw.webp?table=block&id=a0a956e3-9af7-4f8d-aab8-4b2c6e86a141&cache=v2)

It’s not used as often anymore, k8s picked up most of the heat.

#### Core concepts

Services

Tasks

Containers

#### Kubernetes vs Docker swarm

|   |   |
|---|---|
|Kubernetes|Docker swarm|
|Very hard to understand|Much easier to understand|
|Much more prod ready, adopted and used|Not used as often|
|Supports autoscaling|Have to scale it manually|
|Need to install/understand kubectl|Works with the docker cli|
# Architecture

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fbe1569ad-51ef-48bd-9fd8-01e3f11c3432%2Fswarm-diagram.webp?table=block&id=a3b18027-1f74-4e7c-a730-8de851750ae8&cache=v2)

### Manager Node

Manager nodes handle cluster management tasks:

- Maintaining cluster state

- Scheduling services

### Worker Node

Worker nodes are also instances of Docker Engine whose sole purpose is to execute containers.

# Services, tasks, containers

To deploy an application image when Docker Engine is in Swarm mode, you create a service. Frequently a service is the image for a microservice within the context of some larger application (eg - HTTP Server)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fd95ff778-b2c9-4298-bb21-ccc427f267fb%2Fservices-diagram.webp?table=block&id=14fc1df4-52cf-4cd4-8766-4d1c25cbb9bd&cache=v2)

- **Service** - A service is the definition of how you want to run your application in the swarm. It specifies the desired state, including the number of replicas, the image to use, the command to run, and other configurations such as networks and volumes.

- **Task -** A task is a single instance of a service running on a node. Each task represents one container and its associated metadata. When you create a service with multiple replicas, Docker Swarm creates a task for each replica.

- Container - A container is a running instance of a Docker image. Each task maps to one container. The swarm orchestrator ensures the tasks (and thus the containers) are distributed across the nodes in the swarm according to the defined service specifications.
# Create a 2 node swarm

- Create two EC2 machines, install docker in both of them

- Initialise swarm in the first machine

```javascript
docker swarm init
```

- Make the other server join the master (replace the token, ip from the first command)

```javascript
docker swarm join --token b-1-45q02kic0tij84lhkb5du9esm38ly2g6kf3ssm2tq1l6uhwp2s-1i8892561cmfyntnatx97ub1b 192.168.65.3:2377
```

- Make sure the 2377 port on the machine is open

- Confirm the nodes status

```javascript
docker node ls
```
# Deploying a service

- Deploy the nginx service

```javascript
docker service create --replicas 3 --name helloworld -p 3000:80 nginx
```

- Check the status of the service

```javascript
docker service ls
```

- Go to the machine URL on port 3000 and ensure you see it running

```javascript
your_machine_ip:3000
```

- Try deleting a few pods and see if they come back up

- Delete the service

```javascript
docker service rm helloworld
```


