




Build the Docker Image:
```bash
docker build -t go-web-app:v1 .
```

Run the Docker Container:


```bash
docker run -p 8000:8000 go-web-app:v1
```
You should then be able to access it in your browser at http://localhost:8000.





docker login
Tag your local image for Docker Hub:

Bash
```bash
docker tag go-web-app:v1 your-dockerhub-username/go-web-app:v1
```

Push the tagged image to Docker Hub:

```bash
docker push your-dockerhub-username/go-web-app:v1
```


Commit Date: 19-Aug-2025
