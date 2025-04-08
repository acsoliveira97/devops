# Deploy Stage

## Overview
The Deploy stage is where we take our release artifact (the Docker image) and run it in a real or simulated environment. This step validates that the application works as expected when deployed, similar to a production setup.

Deploy the previously tagged Docker image and interact with the application through a local container:
```
docker run -d -p 8080:8080 --name hello-app hello-app:1.0.0
```

You can check the new container using your Docker desktop application or running the following command:
```
docker container list
```

Verify the application is running by opening the browser or using curl:
- Browser: http://localhost:8080/hello
- Via terminal:
```
curl http://localhost:8080/hello
```


## Next Steps
The deployment is complete! Move to the `operate` branch. 
```
git checkout operate
```