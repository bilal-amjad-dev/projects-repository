

[GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker](https://www.youtube.com/watch?v=R8_veQiYBjI&list=PPSV&t=1629s)




**Important links:**

https://github.com/marketplace/actions

https://github.com/marketplace/actions/docker-build-push-action

---


### `on`: name of the GitHub event that triggers the workflow 


### `uses`: whenever we are referring to action in repository we use this attribute
example: action/checkout@v2

### `run`: whenever we are running a command we are using run attribute 
example: run: chmod +x gradlew 


### `runs-on`: ubuntu-latest
Where does this code run?

manage by GitHub (BUT you can also host your own!)

GitHub Action Runner



### `needs`
by default these jobs will run in parallel 

we can override this default parallel execution using needs


### | 
multi-line syntax in yaml







---









Commit Date: 25-Aug-2025
