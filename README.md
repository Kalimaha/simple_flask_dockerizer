[![License](http://img.shields.io/:license-GPL2-green.svg)](http://doge.mit-license.org)

# Simple Flask Dockerizer
Settings to create a Docker image for a simple Flask project. This project has been created for a tutorial described on [Kalimadev Blog](http://wp.me/p61qQI-s).


## Build Docker Container

```
docker build -t simple_flask .
```

The Docker file creates a container starting from Ubuntu 14.04:

```
FROM ubuntu:14.04
```

then it installs Python:

```
RUN apt-get install -y -q build-essential python-gdal python-simplejson
RUN apt-get install -y python python-pip wget
RUN apt-get install -y python-dev
```

and finally creates a virtual environment:

```
RUN pip install virtualenv
```

Required Python projects are installed through ```pip``` in the virtual environment straight from GitHub by setting 
the repositories URL in the ```requirements.txt``` file:

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

## Run Docker Container

```
docker run -it -p 5000:00 simple_flask /deployment/env/bin/python /deployment/start.py
```

This command executes the simple Python script contained in the project to import the main Flask app and run it:

```python
from simple_flask.rest import rest as rest_engine


rest_engine.run_engine('0.0.0.0')
```

The Flask ```host``` has been set to ```0.0.0.0``` in order to work with Docker.

## Access the Application

The application is now up and running and it is possible to access it through the browser at:

```
http://localhost:5000/Kalimaha/
```

that shows:

```
Hello Kalimaha from CORE!
```

The app has a blueprint that can be accessed at:

```
http://localhost:5000/test/Kalimaha/
```

that shows:

```
Hello Kalimaha!
```

Developed with 
--------------
![IntelliJ](http://www.jetbrains.com/idea/docs/logo_intellij_idea.png)
