# Simple Flask Dockerizer
Settings to create a Docker image for a simple Flask project.


## Build the container

```
docker build -t simple_flask .
```

## List Docker Images

```
docker images
```

REPOSITORY      TAG         IMAGE ID            CREATED             VIRTUAL SIZE
simple_flask    latest      b5dc209bf592        5 minutes ago       503 MB

## Run the container

```
docker run -it -p 5000:00 simple_flask /deployment/env/bin/python /deployment/start.py
```
