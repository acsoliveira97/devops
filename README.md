# Operate Stage

## Overview
The Operate stage ensures that the application continues to run smoothly in a deployed environment. 
This includes monitoring the health of the application, reading logs, detecting failures, 
and recovering from issues. In this exercise, we will simulate a common production failure 
and walk through how to detect and fix it using Docker health checks and logs.

Recompile your application:
```
mvn clean install -DskipTests
```

Now lets rebuild the application for a new version:
```
docker build -t hello-app:1.0.1 .
```

Stop and remove the previous container and run a new container:
```
docker stop hello-app && docker rm hello-app
docker run -d -p 8080:8080 --name broken-app hello-app:1.0.1
```

Check the container health status:
```
docker inspect --format='{{json .State.Health}}' broken-app
```

Is there something wrong? You can check your application logs with this command:
```
docker logs broken-app
```

Try and fix the application!

After fixing the application you can redeploy it:
```
mvn clean install
docker build -t hello-app:1.0.2 .
docker stop broken-app && docker rm broken-app
docker run -d -p 8080:8080 --name healthy-app hello-app:1.0.2
```

Now you can rerun the health status of the application:
```
docker inspect --format='{{json .State.Health}}' healthy-app
```

And you can also access our working endpoint:
- Browser: http://localhost:8080/hello
- Via terminal:
```
curl http://localhost:8080/hello
```

