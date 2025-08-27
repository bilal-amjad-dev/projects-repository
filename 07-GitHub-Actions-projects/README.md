This repository has content about GitHub Actions practice files:





### `name:` hello-world

name of the workflow

### `on push`

on push that means whenever something will be committed and pushed on this repository this job should run

### `jobs` : collection of steps

collection of steps (like build, push etc)

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





Source: 

DevOps Shack: https://www.youtube.com/watch?v=kuUHV0I0YwM&list=PPSV

Automation Step by Step: https://www.youtube.com/watch?v=ylEy4eLdhFs&list=PPSV



Commit Date: 27-Aug-2025
