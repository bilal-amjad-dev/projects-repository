In github actions, we do following steps:


- Write Github Actions file
- We store secrets in github repository:
  - dockerusername
  - dockerhub token
  - github token 


# Workflow:

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/8257d72f-00bf-438f-b729-a2d01cd8c7a3" />

- Click Action 

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/048ab55d-177a-4bd9-b237-5e0ac6d39791" />

- Set up a workflow yourself

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/da6dac4f-a0d4-4186-94f8-ff91090c4cfc" />

- write down your GitHub Actions file 

---

# Store Secrets in Github repository:


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/182fb5ac-14fe-4fdb-971f-41300af956ab" />

- Click Settings

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/c1e336c1-753e-4f5f-bf9f-542fdc00f9f4" />

- Secrets and variables
- Actions
- New repository secret

---

## Dockerhub username & token


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/8a1a5d64-d6dd-4b24-84e5-962db129f8dd" />

- Account settings
- Personal access tokens
- Generate new token

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/b21e4ec8-fa7e-4d4f-a58e-716388289c0a" />

- token name
- Read & write

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/5e2dc2e4-719d-4e8d-a9fd-afa78c54d293" />

- Please copy the dockerhub token and note it. because we have to paste it inside **Github repo secrets**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/70c7e499-f137-4b2b-a821-4dca03dfe009" />


<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/24c523df-8ef7-42de-8d89-e8c031c83ddb" />

---

## Github token

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/1c53196f-a1f8-491d-8fdc-e448fa6a7f9d" />

- Github profile
- Settings

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/56372118-82a7-465c-a4af-1d6d5a1ee69d" />

- developer settings

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/6424c4e8-c26c-4a29-b21a-0af88d70ad14" />

- Personal access tokens
- Token (classic)
- Generate new token
- Generate new token (classic)

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/bf6512be-e9de-4cf2-ae94-d52aef9042f5" />

- write token name
- choose repo
- choose write:package 

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/8b0c415f-8289-4f0b-892a-d4bb0f99a92a" />

- Copy and note it because we paste it inside **GitHub repository secret**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/7c8cdc49-af22-4402-b5f6-4908cf4d4d42" />

---

**You can see the 3 secrets stored inside Github repository secret**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/dac386a8-9914-4ae6-b3ff-6261d8bd8c1a" />



Commit Date: 23-Aug-25
