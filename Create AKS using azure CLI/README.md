What is Azure Kubernetes Service (AKS) ?

AKS is a managed Kubernetes service that lets you quickly deploy and manage clusters. We will see how to create AKS cluster in Azure cloud using Azure CLI.

Pre-requistes:

Azure CLI is installed on your local machine.     
Account setup in Azure cloud.                          ![image](https://user-images.githubusercontent.com/113832685/208954356-d6d3d8b0-31de-4df2-8122-a3c1173698cf.png)

Create Resource Group

Step 1

Make sure you are login to Azure portal first.

az login
enter your Microsoft credentials.

Step 2 - create a resource group first.
az group create --name myResourceGroup --location centralus

