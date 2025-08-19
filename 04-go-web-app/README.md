




Build the Docker Image:
```bash
docker build -t your-dockerhub-username/go-web-app:v1 .
```

Run the Docker Container:


```bash
docker run -p 8000:8000 your-dockerhub-username/go-web-app:v1
```
You should then be able to access it in your browser at http://localhost:8080.

Commit Date: 19-Aug-2025
