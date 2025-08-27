This repository has content about GitHub Actions practice files:




|Events|Definition|
|---|---|
|`name:` hello-world|name of the workflow|
|`on push`|on push that means whenever something will be committed and pushed on this repository this job should run|
|`jobs` :|collection of tasks(like build, push etc)|
|`steps`|list of actions|





### `steps` : actions to be taken, commands, scripts

A step is a single instruction or action


## Example

```bash
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4
```

`steps`

This keyword tells GitHub that you are starting a list of individual actions or commands to run.

`- name: Checkout repository`

This is a label or a name for the step.

`uses: actions/checkout@v4`

The actions/checkout action is an official GitHub tool that automatically clones (copies) your GitHub repository onto the runner (the virtual machine) that is running your workflow.


In simple terms, you are telling the pipeline: "The very first thing you need to do is get my code from my repository so you can start working on it."



---

Each task of a job run in GitHub Actions runs on a new, clean virtual machine instance.


This means that the Docker image you build in the build job is not available to the push job. When the push job tries to run docker tag, it won't find the your-app-name:${{ github.sha }} image because it was created and is now gone from the build job's runner.




The key difference here is the use of `actions/upload-artifact` and `actions/download-artifact`. This is the standard way to share data between jobs in GitHub Actions.

This approach is more robust, especially for complex pipelines. However, if you are simply building and pushing, the single-job approach I showed you previously with the `docker/build-push-action` is often simpler and more efficient because it handles a lot of the caching and transfer logic behind the scenes.

---

```bash
# This is a simple CI/CD workflow to build and push a Docker image.
name: CI/CD Pipeline

# The workflow is triggered on every push to the 'main' branch.
on:
  push:
    branches:
      - main
    # Ignore changes to these paths to prevent unnecessary runs
    paths-ignore:
      - 'k8s/**'
      - 'README.md'

# Two separate jobs to handle the build and push stages.
jobs:
  build:
    # Run the job on the latest version of Ubuntu.
    runs-on: ubuntu-latest

    # The steps that will be executed in this job.
    steps:
      # Step 1: Checkout the repository code.
      # This action clones your repository so the workflow can access your files.
      - name: Checkout repository
        uses: actions/checkout@v4

      # Step 2: Build the Docker image.
      # We use 'docker build' to create the image and tag it.
      - name: Build Docker image
        run: docker build -t your-app-name:${{ github.sha }} .

      # Step 3: Save the Docker image as a tar file.
      # This command saves the image locally so we can upload it.
      - name: Save Docker image
        run: docker save -o your-app-name.tar your-app-name:${{ github.sha }}

      # Step 4: Upload the saved image as a workflow artifact.
      # This is the crucial step that makes the image available to the 'push' job.
      - name: Upload Docker image artifact
        uses: actions/upload-artifact@v4
        with:
          name: docker-image-artifact
          path: your-app-name.tar
          retention-days: 1 # Set how long to keep the artifact

  push:
    # This job depends on the 'build' job and will only run after it is successful.
    needs: build
    runs-on: ubuntu-latest

    # The steps that will be executed in this job.
    steps:
      # Step 1: Download the artifact from the 'build' job.
      # This retrieves the tar file containing the Docker image.
      - name: Download Docker image artifact
        uses: actions/download-artifact@v4
        with:
          name: docker-image-artifact

      # Step 2: Load the Docker image from the tar file.
      # This makes the image available on the current runner instance.
      - name: Load Docker image
        run: docker load -i your-app-name.tar

      # Step 3: Log in to Docker Hub.
      # This step uses your stored Docker Hub secrets to authenticate.
      - name: Log in to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      # Step 4: Tag the image with the Docker Hub username and image name.
      # This is required before you can push it to the registry.
      - name: Tag image for push
        run: docker tag your-app-name:${{ github.sha }} ${{ secrets.DOCKERHUB_USERNAME }}/your-app-name:${{ github.sha }}

      # Step 5: Push the Docker image to Docker Hub.
      # The final push command sends the image to your registry.
      - name: Push Docker image
        run: docker push ${{ secrets.DOCKERHUB_USERNAME }}/your-app-name:${{ github.sha }}


```

















Source: 

DevOps Shack: https://www.youtube.com/watch?v=kuUHV0I0YwM&list=PPSV

Automation Step by Step: https://www.youtube.com/watch?v=ylEy4eLdhFs&list=PPSV



Commit Date: 27-Aug-2025
