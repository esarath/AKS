Configure ACR integration for existing AKS clusters | Authenticate with Azure Container Registry from Azure Kubernetes Service

When you're using Azure Container Registry (ACR) with Azure Kubernetes Service (AKS), an authentication mechanism needs to be established. 

To allow an AKS cluster to interact with ACR, an Azure Active Directory managed identity is used. 

Create Resource Group
Make sure you are login to Azure portal first.

az login

You need to create a resource group first.

az group create --name myResourceGroup --location southcentralus

Create AKS cluster with 2 worker nodes

az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 2 --enable-addons monitoring --generate-ssh-keys

az aks show --name myAKSCluster --resource-group myResourceGroup

The above command should display Cluster exists in Azure portal

Create Azure Container Registry

Run the below command to create your own private container registry using Azure Container Registry (ACR).

az acr create --resource-group myResourceGroup --name <acr name> --sku Standard --location southcentralus

Connect to the cluster

 az aks get-credentials --resource-group myResourceGroup --name myAKSCluster --overwrite-existing

To verify the connection to your cluster, use the kubectl get command to return a list of the cluster nodes.

kubectl get nodes

For Deploying Docker images from ACR into AKS Cluster

The following command allows you to authorize an existing ACR in your subscription and configures the appropriate ACRPull role for the managed identity.

az aks update -n myAKSCluster -g myResourceGroup --attach-acr <acr name>

To Detach ACR from AKS use below command

az aks update -n myAKSCluster -g myResourceGroup --detach-acr <acr name>
