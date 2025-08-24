Table of contents

### PCJW

[Install Minikube](#install-minikube)
[Install Jenkins](#install-jenkins)
- [Install plugins in Jenkins](#install-plugin)
- [Add credentials in Jenkins:](#add-credentials)
    - [Dockerhub](#dockerhub)
    - [GitHub](#github)
- [Create Job](#create-job)

[CHANGES](#changes)

- [Add Webhook](#add-webhook)




## Install Minikube
## Install Jenkins
- ### Install plugin


- ### Add credentials

  - **Dockerhub**

 <img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/5d836a62-03a2-479f-8ffd-0bff55b46160" />

- Click **Account settings**
- Click **PAT**
  
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/e5c44917-216f-4d6b-bdc8-21c4f28a51dc" />

- Click **Generate new token**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/ed13b83d-f4fd-4258-9ce4-71f6ac13ecf9" />

- Access token description **dockerhub**
- Access permissions: **Read & Write**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/df91ddd1-92dc-4527-ae59-b1e643c48f36" />

- Please note Personal access token because we have to add in Jenkins Credentials, so that jenkins can access Dockerhub.

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/5fb249da-c27e-40d9-ac12-f9eea248fbbb" />

---

  - **Github**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/68c3069f-9438-46aa-90da-1722dbd0f174" />

- Click **Settings**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/f02c3661-b18e-43a0-b8ec-d6bac818ca68" />

- Click **Developer settings**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/43418f1d-cf1c-4e14-a30c-3975e1dacc84" />

- Click **PAT** > **Token (classic)**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/a44beb3a-ed0c-4854-8d56-625dcb81e55e" />

- Click **Generate new token** > **Generate new token (classic)**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/853b091a-f23f-4acf-9193-515ec371f7d3" />

- Write **PTA** name

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/b5f573c6-7f0c-48ec-9d9f-7e84224f75d3" />

- Select: **repo** **admin:repo_hook** **notifications**


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/ecce208d-b7f3-42b2-ba84-ca356f8f9e8b" />

- Click **Generate token**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/1570f0cb-6f6e-4f75-ad18-e9c133fbbd10" />

- Note **PAT** because we have to add in Jenkins Credentials, so that jenkins can access Github.

---
Now, we have `Dockerhub` token and `Github` token. Now, Add credentials in Jenkins


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/4f465d05-9dcf-4efd-879d-f156cf9b94c7" />

- Click **Manage Jenkins**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/14e25ce6-1132-49d5-851c-57d56e3b7575" />

- Click **Credentials**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/0782e897-921a-46a9-b877-99be38892e07" />

- Click **global**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/80c7d259-ab6e-4d45-b4dd-a588a9e55e3b" />

- Click **Add Credentials**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/aacc58f4-79d7-4fb4-83e6-3f6388bc495d" />

- Username, Password, ID, Description

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/446014c5-792b-4321-aef4-eb332c60b06d" />

- Username, Password, ID, Description

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/3771b0f5-8f08-45b5-8487-8f4cad730728" />

You can see our credentials have stored. 

---

## Creaate Job

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/ed72d2f6-1c06-4903-a0c8-74629118ffeb" />

- Click ***New item*

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/3a023c4b-3580-4ff3-9a74-4eec0f3e8795" />

- Enter **name**
- Click **Pipeline**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/d7be1e47-0440-4b5c-9c74-bc4408171333" />

- Click **GitHub project**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/78648f0b-e9bb-4230-885f-b95b7225fe5f" />

- **Pipeline script from SCM**
- 
- **SCM: Git** 

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/1a1aaf4a-58b5-4458-ac93-9834fc625469" />

- **Repository URL**
- **Branch Specifier: /main**
- Click Save


---

## CHANGES

```bash
DOCKER_IMAGE = 'YOUR-DOCKERHUB-USERNAME/python-flask-app-devops'                                                           // 👈 PASTE YOUR DOCKERHUB-USERNAME HERE
git credentialsId: "${GITHUB_CREDENTIALS}", url: 'https://github.com/YOUR-GITHUB-USERNAME/python-flask-app-devops.git'     // 👈 PASTE YOUR GITHUB-USERNAME HERE
git config user.email "example@example.com"                                                                                // 👈 PASTE YOUR EMAIL HERE 
git config user.name "GITHUB-USERNAME"                                                                                     // 👈 PASTE YOUR GITHUB-USERNAME HERE
```

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/3bcf645f-56a8-4dff-8b25-b40574345bbf" />

- Paste your **DOCKERHUB-USERNAME** and **GITHUB-USERNAME**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/6e26fb3b-483d-4c7f-a3eb-90d70e92dc62" />

- Paste your **DOCKERHUB-USERNAME**

## Add Webhook


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/4cb2766c-6bca-4635-9049-f8d431e1ed4b" />

- Click **Settings**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/9829943a-0571-4f14-8a77-0f52be21a166" />

- Click **Webhooks**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/81d84498-7b99-4626-a6f6-cadc3250f154" />

- Click **Add webhook**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/983567fa-c807-45c7-9609-2fd599097c63" />

- **Payload URL** Paste your Jenkins URL here
- **Content type**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/930ab2f6-7344-4404-a171-3967112b2077" />

- Click **Add webhook**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/633d5462-605d-45da-bf23-dfdbf3e638e7" />

- We cannot save localhost:8080 in **Payload URL**

  














Commit Date: 18-Aug-2025











Commit Date: 24-Aug-2025
