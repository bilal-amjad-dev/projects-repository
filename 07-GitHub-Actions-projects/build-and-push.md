# This workflow uses Docker Buildx to efficiently build and push Docker images.
name: CI with Docker Buildx

on:
  push:
    branches:
      - main
    # Ignore changes to these paths to prevent unnecessary runs
    paths-ignore:
      - 'k8s/**'
      - 'README.md'

jobs:
  docker:
    runs-on: ubuntu-latest
    steps:
      # Step 1: Checkout the repository code.
      # This action clones your repository so the workflow can access your files.
      - name: Checkout repository
        uses: actions/checkout@v4

      # Step 2: Set up Docker Buildx.
      # This initializes the Buildx environment, which provides advanced
      # Docker build capabilities like improved caching.
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      # Step 3: Log in to Docker Hub.
      # Authenticates with Docker Hub using your stored secrets.
      # These secrets must be configured in your GitHub repository settings.
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }} # Use secrets for credentials
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      # Step 4: Build and push the Docker image.
      # This action combines building the image and pushing it to Docker Hub.
      # It leverages Buildx for efficiency.
      - name: Build and push Docker image
        uses: docker/build-push-action@v6
        with:
          context: . # Use the current directory as the build context
          push: true # Set to true to push the image to Docker Hub
          tags: | # Define multiple tags for the image
            ${{ secrets.DOCKERHUB_USERNAME }}/your-app-name:latest
            ${{ secrets.DOCKERHUB_USERNAME }}/your-app-name:${{ github.sha }}
          # The 'platforms' line is commented out as QEMU was removed,
          # meaning we are now building for the default architecture (linux/amd64).
          # platforms: linux/amd64,linux/arm64



Commit Date: 28-Aug-2025
