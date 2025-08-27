
This is very very important folder.

This person covers very very important steps:

---





GitHub Actions

Feature in GitHub to create custom Automated Workflows

automate SDLC workflows

implement CI CD DevOps

 DEMO
 
 Step 1 - Signup and Login to GitHub.com
 
 Step 2 - Create a new Repository
 
 Step 3 - In the repo create a folder .github/workflows
 
 Step 4 - In the folder create a YAML file with .yml extension
 
 Step 5 - Add the content of the workflow in the file
 
 Step 6 - Commit and push the changes
 
 Step 7 - Goto Repo main page and click “Actions” tab
 
 Step 8 - Select the workflow from left sidebar and check the logs and results

 Terms:
 
 WORKFLOW : collection of jobs, defined in a YAML file
 
 name:
 
 EVENTS : any activity in the repo that can trigger a workflow 
 
 on:
 
 JOBS : collection of steps
 
 jobs:
 
 STEPS : actions to be taken, commands, scripts
 
 steps:
 
 Chain Jobs - :needs



```bash
name: hello-world
on: push
jobs:
  my-job:
    runs-on: ubuntu-latest
    steps:
      - name: my-step
        run: echo "Hello World!"
```









---

### Terms:
1. Workflows
2. Events
3. Jobs
4. Steps 


- Google:

github actions yaml to print hello world 

https://gist.github.com/weibeld/f136048d0a82aacc063f42e684e3c494


- Google:

YAML formatter 



Event:

you can see here the event is `on push` that means whenever something will be committed and pushed on this repository this job should run

- YouTube:

https://www.youtube.com/watch?v=ylEy4eLdhFs










Commit Date: 27-Aug-2025
