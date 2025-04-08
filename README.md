# Release Stage

## Overview
In this stage, we prepare and tag a Docker image to mark a versioned release of the application. This image represents a portable and deployable build that can be shared across environments.

In real-world pipelines, release management is often automated using CI/CD tools.
For this exercise, we'll simulate that by creating and tagging a Docker image locally.

Ensure your application is built:
```
mvn clean install
```

Build a Docker image using the generated .jar file:
```
docker build -t hello-app:1.0.0 .
```

You can check your new image using the Docker Desktop application or running the following command:
```
docker image list
```

## Next Steps
Move to the `deploy` branch to run the released Docker image in a container.
```
git checkout deploy
```