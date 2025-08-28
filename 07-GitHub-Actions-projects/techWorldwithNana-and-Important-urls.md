

[![GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker](https://img.youtube.com/vi/R8_veQiYBjI/mqdefault.jpg)](https://www.youtube.com/watch?v=R8_veQiYBjI)

**Important links:**

https://github.com/marketplace/actions

https://github.com/marketplace/actions/docker-build-push-action

---



|Event|Definition|
|---|---|
|`needs| by default these jobs will run in parallel. We can override this default parallel execution using needs|
|`runs-on`| Where does this code run? GitHub Action Runner. manage by GitHub (BUT you can also host your own!) |
|`on`| name of the GitHub event that triggers the workflow |
|`uses`| whenever we are referring to action in repository we use this attribute, example: action/checkout@v2|
|`run`|  whenever we are running a command we are using run attribute, example: run: chmod +x gradlew  |

|`|`| multi-line syntax in yaml|


---

https://github.com/marketplace/actions/docker-login

**This is About GitHub Action to login against a Docker registry.**

---






Commit Date: 25-Aug-2025

Commit Date: 27-Aug-2025
