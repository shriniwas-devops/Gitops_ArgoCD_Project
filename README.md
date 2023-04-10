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



