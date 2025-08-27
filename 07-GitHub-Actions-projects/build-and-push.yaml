name: Build and Push Docker Image

on:
  push:
    branches:
      - main  # Trigger workflow on push to main branch

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
      # Step 1: Checkout the repository
      - name: Checkout repository
        uses: actions/checkout@v4  # Clones the repo to access code

      # Step 2: Log in to Docker Hub
      - name: Log in to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      # Step 3: Build Docker image
      - name: Build Docker image
        uses: docker/build-push-action@v5
        with:
          context: .  # Use repository root as build context
          push: false  # Do not push, only build
          tags: |
            ${{ secrets.DOCKERHUB_USERNAME }}/flask-hello-world:latest
            ${{ secrets.DOCKERHUB_USERNAME }}/flask-hello-world:${{ github.sha }}

      # Step 4: Push Docker image
      - name: Push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .  # Use repository root as build context
          push: true  # Push the image to Docker Hub
          tags: |
            ${{ secrets.DOCKERHUB_USERNAME }}/flask-hello-world:latest
            ${{ secrets.DOCKERHUB_USERNAME }}/flask-hello-world:${{ github.sha }}
