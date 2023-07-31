# Docker

### What is Docker?
Docker is an open-source platform that allows you to automate the deployment, scaling, and management of applications inside lightweight, portable containers. Containers are isolated environments that package everything needed to run an application, including code, runtime, libraries, and dependencies. Docker makes it easier to develop, ship, and run applications consistently across different environments.

### Key Concepts
#### Images: 
Docker images are the blueprints used to create containers. They are read-only templates that contain all the necessary instructions to create a runnable application.

#### Containers: 
Containers are instances of Docker images. They are isolated environments where the application can run without affecting the host system or other containers.

#### Dockerfile: 
A Dockerfile is a text file containing a set of instructions that specify how to build a Docker image. It includes details such as the base image, application code, dependencies, and configurations.

#### Registry: 
Docker Hub is the default public registry where you can find and share Docker images. You can also use private registries to store your own images.


### Docker Examples
Let's walk through some basic examples to understand how Docker works:

#### Example 1: Running a Hello World Container
 1. Install Docker: Ensure you have Docker installed on your system. You can download Docker Desktop (for Windows and macOS) or Docker Engine (for Linux) from the Docker website.
 2. Open a terminal or command prompt.
 3. Pull a Docker image: To run a container, you need an image. Let's start with a simple one, like the "hello-world" image:

```
docker pull hello-world
```

**Run the container:**
```
docker run hello-world
```
You'll see a message indicating that the container is running. It will print "Hello from Docker!" along with some additional information.

#### Example 2: Building a Custom Image
Let's create a custom Docker image for a simple Python web application.

- Create a new directory for the project and navigate into it:
```
mkdir my_python_app
cd my_python_app
```

- Create a file named app.py and add the following Python code:

```
# app.py
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, Docker World!"

if __name__ == '__main__':
    app.run(host='0.0.0.0')
```

- Create a file named Dockerfile (no file extension) in the same directory and add the following content:
```
# Dockerfile
FROM python:3.9

WORKDIR /app

COPY app.py /app

RUN pip install flask

CMD ["python", "app.py"]
```

- Build the Docker image:
```
docker build -t my-python-app .
```
The -t flag assigns a name (my-python-app) to the image.

- Run the container using the custom image:
```
docker run -p 8080:5000 my-python-app
```

The -p flag maps port 8080 of the host to port 5000 inside the container.
You can access the web application by opening a web browser and navigating to 
`http://localhost:8080`.



### Summary
Docker simplifies the process of managing applications and their dependencies by using containers. It allows you to create, distribute, and run applications consistently across different environments. This tutorial covered the basics of Docker, including definitions and practical examples to help you get started.
Keep exploring Docker's rich ecosystem and various features to harness the full potential of containerization in your development and deployment workflows!























