# Notes--Docker

[Infrastructure As Code](https://martinfowler.com/bliki/InfrastructureAsCode.html)

- Create a `Docker File` in the same directory as the app.

Example:

```
FROM ubuntu:latest

# Commands to run to install dependencies
RUN apt-get update -y
RUN apt-get install -y python3

#When you pass commands to the container, what should interpret them
ENTRYPOINT ["python3"]

# Command to run when the container starts
CMD ["app.py"]

# Working directory
WORKDIR /app

#Copy apps from the local folder to the Docker container
COPY app.py app.py
COPY alternate.py alternate.py

Make port available
EXPOSE 8080
```

1. Create the `Docker Image`. `build -t app-name-here .`
  - Builds a Docker image with the tag of "app-name-here" in the current directory.
1. Confirm your build with `docker images command`.
1. Create a container based on the image.
  - `docker run -p 8080:8080 app-name-here`
  - Select the tag.