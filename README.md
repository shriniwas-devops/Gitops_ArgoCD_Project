Grand Real-time End to End DevOps CI/CD Project | Git | Jenkins | Docker | K8's | ArgoCD 

Project Architecture

<img width="2630" alt="YTUTUYT" src="https://user-images.githubusercontent.com/122585172/230826915-148747bf-59c9-4f04-ae1b-20c20d139440.png">

Prerequisites:
1. Minikube Cluster
2. Kubectl installed
3. Docker Installed on Jenkins

Some Project Info we will coverd:

 [1] Trigger CD Jenkins Job using CurL command and Pass variables from CI pipelines.
- [2] Connect private GitHub Repo to ArgoCD for CD part.
- [3] Connect Kubetnetes node to ArgoCD
- [4] Kubernetes Manifest file creation
- [5] Dockerizing python application
- [6] Python Application Overview
- [7] WebHook Configurations
- [8] Server setup & Installations
- [9] Trigger Jenkins Job using VS Code Itself
- [10] Jenkins Runner configuration
- [11] Advance Declarative Jenkinsfile creation(Groovy Scripting)

 CI/CD PIPELINE WORKFLOW:

So this is what developer do , developer  writing a python code , and he will pushed to guthub once he will pushed in github , what will be idle 
situation jenkins should automatically pull the letest code and apply . there will be various stages over there, so we will be triggering this job using webhook, and we will writing dockerfile for conatinrization python application along with that , aprt from that dockerizing the application and we will conatinrization application as weel. so here we will be using kubernetes as a orchestration tool so for that we will writing manifest file which will have deployment and services we will expose our application and so here we go we are including argoCD we are using ArgoCD which will do what which will trigger latest changes and it will apply to your minikube cluster.

So CD part will be taken care by ArgoCD .

Push all the web application page code file into github:

![fghgfhfg](https://user-images.githubusercontent.com/122585172/230832698-aa8f6803-498d-49e5-8cec-a8611f0cb749.png)

Jenkins Runner configuration:

Create .vscode folder/create settings.json file/go to extension/ search jenkins runner plugin/install the plugin

![dfgdg](https://user-images.githubusercontent.com/122585172/230833257-b6071b4e-5a45-4d98-83cd-42fa340da06e.png)


For Install jenkins you can follow here:https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

After Install jenkins look like this:

![fdgfdg](https://user-images.githubusercontent.com/122585172/230833849-6ce83862-41ad-4116-88e9-e7f7da26f466.png)

For docker Install  &   create Dockerhub  account:

For install docker:https://docs.docker.com/engine/install/ubuntu/

And Dockerhub account you look like this:

![dsfdsf](https://user-images.githubusercontent.com/122585172/230834301-a14cc0e7-7d45-459e-8d9f-73fca11df0f8.png)

For Minikube install you van follow: https://minikube.sigs.k8s.io/docs/start/

 For ArgoCD you need to follow this: https://argo-cd.readthedocs.io/en/stable/getting_started/
 
 After install argoCD look like this:
 
![dfgfd](https://user-images.githubusercontent.com/122585172/230836035-f6a27faf-70ea-438d-ac6d-51777f1ba477.png)

 Now Create a declarative jenkins pipeline for each stage.
 
 
 Stage 01: Cleanup workspace
 
 1. whatever change you done with it will copy of version file to github your jenkins so that we don't need you clean up previous thing .
 2. we have to call the function that is cleanWs().

![dsfdsfds](https://user-images.githubusercontent.com/122585172/230838551-ebfd8ad9-9053-4c55-bf8e-d7d0f28247d1.png)

So let's do one thing let's add our environment variables first so environment variables why we will using we will be using to hide our Github secretes and our dockerhub serectes hwo we can declare env.

![sadsads](https://user-images.githubusercontent.com/122585172/230840996-a1479a71-3ab8-4b47-9fca-4aa60f112463.png)

Stage 02: checkout scm

1. Go to pipeline syntax/select withcredentials/select username or password/and then click on genrate pipeline syntax.

![fdssdd](https://user-images.githubusercontent.com/122585172/230842515-5f100bcc-0560-45b8-86dd-b0554cba686c.png)

Make sure you install docker pipeline and dashboard  view plugin.

Stage 03: Build Docker iamge

1. here what we will do we will calling docker variable and we have to build our dockerfile so that's why docker build and here you have the provide the imagename .
2. once you  will compile the docker file what is the image youn want to create .

![fdgfdg](https://user-images.githubusercontent.com/122585172/230843716-b54460a9-84ba-4d33-8939-a835f2eaf181.png)

Dockerfile :

![sdfdsf](https://user-images.githubusercontent.com/122585172/230843967-0640c689-7bcd-4870-bfe6-7b6be1d24312.png)

1. From base image i will using ppython:3.9-slim-buster then i will be runing .
2. then i will be create conatiner work directory and then we will copy our app.py to the work directory of  conatiner.
3.  and then by default port exposed 5000 and make the application keep executing backend 
4.  whenever you create conatiner something should there inside that will keep on executing either it's  for java -jar or for python python


Stage 04: Push Docker Image

1. Here what we have to do in ordered push your images in dockerhub you have to first login to the authenticate with dockerhub. 
2. we are pushing just one image with build number


![gfdhgfdh](https://user-images.githubusercontent.com/122585172/230845930-041f0b3c-4c3f-437c-85b6-eb5dd904e737.png)


Stage 05: Delete Docker Image

1. so first image we have to clean what are the image name we have , we have the image name with application name and the tag(latest).

![fdgfdfd](https://user-images.githubusercontent.com/122585172/230846606-f2344653-f915-4989-90d8-fb8bcd7839cc.png)


Deployments.yml file:

![gfdfd](https://user-images.githubusercontent.com/122585172/230846903-d4e84d44-4311-46e7-92fd-18799c47f4da.png)

Service.yml file:


![fgfdg](https://user-images.githubusercontent.com/122585172/230889841-b65846fe-47b2-4f42-af53-1182d40e530a.png)



Stage 06: updating kubernates deployments file


![FGHFFH](https://user-images.githubusercontent.com/122585172/230889941-b003db45-e748-43cf-bbad-f1bdab45d178.png)


1. First thing what will have to do we will printing what is the current deployment.yml file we have it will print the same version.
2. Later what we have to do i will be using set commad here  so string with my application we wil replace v1 with jenkins build number.
3 again we will check  deployment file either the version has been change or not.


Stage 07: push the changed deployment file to git


![HGJGHJG](https://user-images.githubusercontent.com/122585172/230890050-46d539f4-4a19-46c2-8d05-3e8be558a23b.png)


1. so it will do what it will update our current jenkins file and it will pushed to the git again .
2. this is user it will pushed the file back the it will try the pushed the file where we have the updated the version again same  github repository.


OUTPUT:

Jenkins output:

![FHFG](https://user-images.githubusercontent.com/122585172/230891959-cf71e666-4de8-4b8e-a41a-ce331112338d.png)


Dockerhub:

![ghjgh](https://user-images.githubusercontent.com/122585172/230892199-feb0acde-2901-4840-8397-4461451efcff.png)

ArGoCD output:

![fghfghfg](https://user-images.githubusercontent.com/122585172/230892799-370a3493-eb0d-44ec-9bbc-ce8e9bbfb55f.png)


![jhhgjhgj](https://user-images.githubusercontent.com/122585172/230893335-1a9f9b2d-9aff-448f-b243-a61f64cd857e.png)


