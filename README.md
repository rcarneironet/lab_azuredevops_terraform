#Getting started

Before getting started working with Terraform in Azure DevOps, make sure to create a Storage account in Azure and provision a Container. This container will be used by Terraform to keep its state updated. Refer to this [document](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal) in order to create a storage account in the Azure Portal.

As a next step, create an Azure DevOps project to version a Git repository to run a CI pipeline. Refer to this [document](https://docs.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&amp;tabs=preview-page) to get it done. Additionally, you&#39;ll need to install Terraform extension for Azure DevOps. Visit [this link](https://marketplace.visualstudio.com/items?itemName=ms-devlabs.custom-terraform-tasks) to get it done.

**Option 1) Setting up CI pipeline using Terraform in Azure DevOps**

The way it works is quite simple. Just create a new pipeline in Azure DevOps and point to file &quot;sample-azure-pipelines.yaml&quot; which is the file responsible to run the pipeline in Azure and provision the infrastructure.

As we can see, there are many variables that would need to be filled out, such as:

- **azure\_subscription\_id** - You&#39;ll need to grant access from Azure DevOps to an Azure subscription to be able to deploy resources. This can be easily found in &quot;Project settings&quot; then &quot;Service connections&quot; menu. Just set up a new connection.
- **resource\_group\_name** - This is the resource group in which resources will be deployed within Azure.
- **storage\_account\_name** - This is the storage account you&#39;ll need to create in Azure. This is needed because Terraform needs a storage to maintain its states.
- **container\_terraform** - This is the container you&#39;ll need to create in your storage account. Both are needed to enable this pipeline to work.

![](https://github.com/rcarneironet/lab_azuredevops_terraform/blob/main/images/ci-terraform-setup.png)

**Option 2) Create a CI pipeline using Azure DevOps GUI**

In this case, if we prefer to create the pipeline using the graphical interface, make sure to add the following tasks and configurations:

Terraform Install task

![](https://github.com/rcarneironet/lab_azuredevops_terraform/blob/main/images/ci-terraform-task1.png)

Terraform Init task

![](https://github.com/rcarneironet/lab_azuredevops_terraform/blob/main/images/ci-terraform-task2.png)

Terraform Plan task

![](https://github.com/rcarneironet/lab_azuredevops_terraform/blob/main/images/ci-terraform-task3.png)

Terraform Validate and Apply Task 
![](https://github.com/rcarneironet/lab_azuredevops_terraform/blob/main/images/ci-terraform-task4.png)
