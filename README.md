# Trigo-infra

## Pre-requirements
1) Create my own Helm repo for each app on GitHub with GitHub pages
2) Create my own Docker repo for each app on Docker Hub
3) Install Jenkins "Active Choices" plugin for injecting env params 
4) Configure GitHub webhook for each app repo fir triggering appA & appB pipeline


## Detailed plan
1) Write 2 similar Flask servers python apps & Jenkinsfiles & Dockerfiles 
2) Helm upgrade is triggered with every code or configuration update.
   This is due to GitHub webhook.
3) Each app will have its own GitHub repo & Jenkinfile & Helm repo
4) Each app will have its own configuration params ENV & REGION. 
4) Each app will have its own configuration param REPLICAS for scaling
5) Each Jenkinfile will clone the app repo & build a docker image
6) If docker build success push image to DockerHub
7) Add Helm repo & update repo
8) Deploy helm chart with relevant configuration 
9) Clone the infrastructure repo "Trigo-infra" in order to deploy apps-ingress
10) Open sites appA.com & appB.com and see the miracle happens :)
