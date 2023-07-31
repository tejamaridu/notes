# Podman

### What is Podman?

Podman is an open-source containerization tool that allows you to create, manage, and run containers and pods. Like Docker, Podman provides a way to package applications and their dependencies into isolated containers. However, unlike Docker, Podman does not require a central daemon to run containers, and it can be used without root privileges, making it more secure and user-friendly.

### Key Concepts

1.  Containers: Containers in Podman are the same as in Docker. They are isolated environments that encapsulate an application and its dependencies.

2.  Pods: A Pod is a group of one or more containers that share the same network namespace and can communicate with each other using `localhost`. Pods provide a way to manage multiple containers as a single unit.

3.  Images: Podman images are similar to Docker images. They are read-only templates used to create containers.

4.  Rootless: Podman can be run without root privileges, allowing regular users to work with containers safely.

### Podman Examples

Let's go through some basic examples to get you started with Podman:

#### Example 1: Running a Hello World Container

1.  Install Podman: Ensure you have Podman installed on your system. It comes pre-installed on some Linux distributions, or you can install it via your package manager.

2.  Open a terminal or command prompt.

3.  Pull a Podman image: Just like Docker, Podman uses container images. We'll start with the "hello-world" image:
```podman pull hello-world```

1.  Run the container:
`podman run hello-world`

The output will show a message indicating that the container is running and display "Hello from Docker!" along with some additional information.

#### Example 2: Building and Running a Custom Container

Now let's build and run a custom container using Podman:

1.  Create a new directory for the project and navigate into it:
```
mkdir my_app
cd my_app
```

2.  Create a file named `app.py` and add the following Python code:
```
# app.py
print("Hello, Podman World!")
```

3.  Build the container image:
```
podman build -t my-python-app .
```

The `-t` flag assigns a name (`my-python-app`) to the image.

4. Run the container:
```
podman run my-python-app
```

You should see the output "Hello, Podman World!" printed in the terminal.

#### Example 3: Creating and Managing a Pod

Now let's create a Pod containing two containers:

1.  Create a new directory for the project and navigate into it:
 
```
mkdir my_pod
cd my_pod
```

2.  Create two simple shell scripts named `app1.sh` and `app2.sh`:
```
# app1.sh
#!/bin/sh
echo "Running App 1..."
sleep 10
echo "App 1 finished."
```

```
# app2.sh
#!/bin/sh
echo "Running App 2..."
sleep 10
echo "App 2 finished."
```

3.  Make the scripts executable:
```
chmod +x app1.sh app2.sh
```

4.  Create a Pod specification file named `my-pod.yaml`:
```
# my-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: container1
      image: alpine
      command: ["/bin/sh", "-c", "./app1.sh"]
    - name: container2
      image: alpine
      command: ["/bin/sh", "-c", "./app2.sh"]`
```

5.  Create the Pod:
```
podman play kube my-pod.yaml
```

This will create the Pod with two containers. Each container will run its respective script, wait for 10 seconds, and then finish.

6.  View Pod status:
```
podman pod ps
```

You should see the status of the containers within the Pod.

### Conclusion
Podman is a versatile containerization tool that provides similar capabilities to Docker but with the added advantage of running without a central daemon and supporting rootless containers. This tutorial covered the basics of Podman, including definitions and practical examples to help you get started.
Explore Podman's features and functionalities further to leverage its benefits in your container workflows, especially if you value security and a daemonless experience.
