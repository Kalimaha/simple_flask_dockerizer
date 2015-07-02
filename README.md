# Simple Flask Dockerizer
Settings to create a Docker image for a simple Flask project.


## Build the container

```
docker build -t simple_flask .
```

The Docker file create a container starting from Ubuntu 14.04:

```
FROM ubuntu:14.04
```

then install Python:

```
RUN apt-get install -y -q build-essential python-gdal python-simplejson
RUN apt-get install -y python python-pip wget
RUN apt-get install -y python-dev
```

then it creates a virtual environment:

```
RUN pip install virtualenv
```

Required Python projects are installed by ```pip``` straight from GitHub by setting the repositories URL in the 
```requirements.txt``` file:

```
watchdog
Flask
flask-cors
https://github.com/Kalimaha/simple_flask/archive/master.zip
https://github.com/Kalimaha/simple_flask_blueprint/archive/master.zip
```


## List Docker Images

```
docker images
```

|REPOSITORY|TAG|IMAGE ID|CREATED|VIRTUAL SIZE|
|----------|---|--------|-------|------------|
|simple_flask|latest|b5dc209bf592|5 minutes ago|503 MB|

## Run the container

```
docker run -it -p 5000:00 simple_flask /deployment/env/bin/python /deployment/start.py
```

This command execute the simple Python script contained in the project, that imports the main Flask app and runs it:

```python
from simple_flask.rest import rest as rest_engine


rest_engine.run_engine('0.0.0.0')
```

The Flask ```host``` has been set to ```0.0.0.0``` in order to work with Docker.
