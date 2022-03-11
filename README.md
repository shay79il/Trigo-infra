# Trigo-infra

## Pre-requirements
1) Create my own Helm repo for each app on GitHub with GitHub pages
2) Create my own Docker repo for each app on Docker Hub
3) Install Jenkins "Active Choices" plugin for injecting env params 
4) Configure GitHub webhook for each app repo fir triggering appA & appB pipeline
5) In order for the GitHub webhook to work we use ngrok linux app to expose our localhost port 80
6) Make sure Jenkins wil know k8s and helm by these 2 commands
   1) sudo cp .kube/config ~jenkins/.kube/config
   2) sudo chown jenkins: ~jenkins/.kube/config


## Detailed plan
1) Write infrastructure repo for apps-ingress
2) Write 2 similar Flask servers python apps & Jenkinsfiles & Dockerfiles
3) Helm upgrade is triggered with every code or configuration update.
   This is due to GitHub webhook.
4) Each app will have its own GitHub repo & Jenkinfile & Helm repo
5) Each app will have its own configuration params ENV & REGION. 
6) Each app will have its own configuration param REPLICAS for scaling
7) Each Jenkinfile will clone the app repo & build a docker image
8) If docker build success push image to DockerHub
9) Add Helm repo & update repo
10) Deploy helm chart with relevant configuration 
11) Clone the infrastructure repo "Trigo-infra" in order to deploy apps-ingress
12) Configur on the localhost at /etc/hosts the apps URL in order to surf to the right app
    1) 192.168.59.100	app-a.com
    2) 192.168.59.100	app-b.com
13) Open sites app-a.com & app-b.com and see the miracle happens :)
