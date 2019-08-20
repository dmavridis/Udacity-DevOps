# Capstone Project 

## Scope the Project

The purpose of this Project is to develop a simple application applying the principles of CI/CD and GitOps, using Kubernetes. 

Due to  small experience with DevOps, I decided to use a very simple application, that includes an `index.html` file, which is deployed to a Docker image of an Nginx server, as shown in the following pipeline. 

![pipeline](images\pipeline.png)

After thorough search, I decided to use Jenkins-X due to its native support for Kubernetes and I also wanted to experiment. Due to the simplicity of the application, I found it easier to use rolling deployment; any change is directly applied to the application. 

I followed the setup instructions for AWS (described in <https://aws.amazon.com/blogs/opensource/continuous-delivery-eks-jenkins-x/>), I was able to install the cluster by executing the command

```javascript
jx create cluster eks --cluster-name=dimicloud --skip-installation=true
```

but the next step

```
jx install --provider=eks --default-environment-prefix=dimicloud
```

was never completing. I googled the issue and other people had the same issue without any solution existing. After spending a significant amount of time, as a result, I decided to switch to Google Cloud Platform (GCP), despite the fact that I didn't have any experience with this platform. The issue, is that some features that I used in AWS in the previous project such as linting, I was not able to implement in GCP. 

Starting over with creating a new cluster executing the command:

```
jx create cluster gke --min-num-nodes=2 --max-num-nodes=2 --skip-login
```

and it was competed successfully deploying two nodes and returning the following log file:

```
our Kubernetes context is now set to the namespace: jx
To switch back to your original namespace use: jx namespace default
Or to use this context/namespace in just one terminal use: jx shell
For help on switching contexts see: https://jenkins-x.io/developing/kube-context/
To import existing projects into Jenkins:       jx import
To create a new Spring Boot microservice:       jx create spring -d web -d actuator
To create a new microservice from a quickstart: jx create quickstart
Fetching cluster endpoint and auth data.
kubeconfig entry generated for shiftlake.
Context "gke_stellar-orb-126418_europe-west1-b_shiftlake" modified.
NAME              HOSTS                                      ADDRESS          PORTS   AGE
chartmuseum       chartmuseum.jx.35.187.176.187.nip.io       35.187.176.187   80      5m35s
docker-registry   docker-registry.jx.35.187.176.187.nip.io   35.187.176.187   80      5m36s
jenkins           jenkins.jx.35.187.176.187.nip.io           35.187.176.187   80      5m36s
nexus             nexus.jx.35.187.176.187.nip.io             35.187.176.187   80      5m36s
```

![nodes](C:\Users\mavridis\OneDrive - Qualcomm\Documents\udc\Capstone\images\nodes.png)



## Jenkins-X installation

Jenkins-X comes with some project templates. Since the application I wanted to use is similar to the one of the templates that creates a docker image running php, I created that template and modified the docker image accordingly. Doing this process the code scafolding is implemented, as shown in the github <https://github.com/dmavridis/Udacity-DevOps>

The initial webpage looks like the screenshot. 

![version1](images\version1.png)

Doing a small change in the html file, after a few minutes a new version is up as shown in the following screenshots:



![1566341023889](images\steps.png)

![version2](images\version2.png)





