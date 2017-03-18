![scaleconf-deploying-microservices](kubernetes.png)


#Run and expose container on Kubernates

##Publish image in a Docker registry

We need to publish our image in a private or public registry

`Public`
* Docker hub https://hub.docker.com/

`Private`
* Azure container registry https://azure.microsoft.com/en-us/services/container-registry/
* AWS container registry https://aws.amazon.com/es/ecr/
* Google Cloud container registry https://cloud.google.com/container-registry/
* etc 

This time we're going to use Docker Hub, we need to execute the next commands

```sh
$ docker login
$ Username: <dockerhub user>
$ Password: <dockerhub password>
```

Then we need to create a tag for our microservice image

```sh
$ docker tag microservice <username>/scaleconf
$ docker push <username>/scaleconf
```
Check your Docker Hub account 


##Run container on Kubernetes

We can create and configure a Kubernetes inside a virtual machine cluster but that takes a lot of expertise and time. We can take advantage of different cloud platforms like:  

`Google`
* https://cloud.google.com/container-engine/ 

`Azure`
* https://azure.microsoft.com/en-us/services/container-service/

`AWS`
* https://aws.amazon.com/es/quickstart/architecture/heptio-kubernetes/


#Azure Container Services

Install Azure Commanline Tool 2.0 
* https://docs.microsoft.com/en-us/cli/azure/install-azure-cli 

Create Kubernetes Cluster 
```sh
az login -u <subscriptionuser>
az acs create --orchestrator-type=kubernetes --resource-group <RESOURCE_GROUP> --name=<CLUSTER_NAME> --dns-prefix=<DNS_PREFIX>
```
Install Kubernetes command line tool
```sh
az acs kubernetes install-cli
```
Connect to a cluster 
```sh
az acs kubernetes get-credentials --resource-group=<RESOURCE_GROUP> --name=<CLUSTER_NAME>
```



