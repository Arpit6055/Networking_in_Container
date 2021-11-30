# Networking_in_Container
we will see how can we connect 2 containers running on a VM or a server

## Installation

First install [docker](https://www.docker.com/products/docker-desktop)

Now Download the code source for this project.

Open Your terminal and open this project's directory.

## Usage

```CMD
docker network create --driver=bridge app-net

// This will download the docker image of mongodB//
docker run -d --network=app-net -p 27017:27017 --name=db --rm mongo:3


```

We have exposed our mongo container on port:27017 of the local machine.

We have added the "npm ci " command in the Dockerfile itself for proper containerization and included all the non required files like .git and node_module in .dockerignore file.

so you can directly give the command to build the docker image and run it
```CMD
docker build --tag=my-app-with-mongo .
docker run -p 3000:3000 --network=app-net --env MONGO_CONNECTION_STRING=mongodb://db:27017 my-app-with-mongo

```
If you followed all the steps correctly, then both your containers will be running and connected to each other.
first click here  [add](http://localhost:3000/add)
click on add for multiple times and then open the [home](http://localhost:3000/).
you will see every time you visit the add page and return back to home, the count will increase by one

