# jenkins-docker-acr-aks-pipeline
End-to-end DevOps CI/CD project using Git, Jenkins, Docker, Azure Container Registry (ACR), and Azure Kubernetes Service (AKS) to automate application build, containerization, and deployment.
## **1. Project Overview**

This project demonstrates the implementation of an end-to-end DevOps CI/CD workflow to automate application build, containerization, image management, and deployment using Jenkins and Microsoft Azure services.

The project integrates Git for source code management, Jenkins for CI/CD automation, Docker for containerization, Azure Container Registry (ACR) for storing container images, and Azure Kubernetes Service (AKS) for container orchestration and application deployment.

The primary objective is to reduce manual deployment activities, improve deployment consistency, and demonstrate practical implementation of DevOps practices using cloud-native technologies.

## **2. Project Objectives**

Implement source code management using Git and GitHub.

Configure Jenkins to automate application build and deployment workflows.

Containerize the application using Docker.

Push and manage Docker images in Azure Container Registry.

Deploy containerized applications to Azure Kubernetes Service.

Understand the integration between CI/CD tools and Azure cloud services.

Perform deployment verification and basic troubleshooting.

## **3. Project Architecture**

The project follows a DevOps workflow connecting source code management, CI/CD automation, container image management, and Kubernetes deployment

   <img width="1774" height="887" alt="architecture_diagam" src="https://github.com/user-attachments/assets/51ac5802-81e4-430c-88ea-728c77e564e9" />

### **Technology Flow:**

GitHub → Jenkins → Docker → Azure Container Registry → Azure Kubernetes Service → Running Application

### **Source Code Management Using Git**
Git is used to manage application source code and track changes throughout the development process.

GitHub acts as the remote repository for storing and maintaining project files.

Key operations include:

- Initializing the Git repository.
- Adding and committing source code.
- Pushing changes to GitHub.
- Maintaining the application source code in a centralized repository.

<img width="807" height="287" alt="fwef" src="https://github.com/user-attachments/assets/05ab59c1-af6b-4121-917a-e612abc4a093" />
<img width="859" height="235" alt="vsdava" src="https://github.com/user-attachments/assets/d6757b86-1a53-4a14-b78b-7ea941649c17" />
<img width="989" height="274" alt="vsdvaa" src="https://github.com/user-attachments/assets/67e2b018-59ce-4d13-924c-67cc8fb28981" />

### **Jenkins Configuration and CI/CD Automation**
Jenkins is configured to automate the application build and deployment workflow.

The Jenkins job integrates with the GitHub repository to retrieve the latest application source code and execute the configured build operations.

Key implementation activities:

- Configuring Jenkins.
- Integrating the GitHub repository.
- Configuring the required build tools.
- Executing application build operations.
- Integrating Docker image creation into the workflow.
- Configuring authentication for the required container registry.
- Monitoring build execution through Jenkins console output.

Jenkins helps reduce repetitive manual operations and provides visibility into the build process.

**Use maven pipeline for java application**
<img width="1366" height="615" alt="jen_1" src="https://github.com/user-attachments/assets/8a1fea8b-317a-4eac-a443-3631eb9313ee" />
**Install Maven integration plugin**
<img width="843" height="379" alt="jen_5" src="https://github.com/user-attachments/assets/128b3388-ec9a-411d-9196-cf76426602f2" />
**Under configuration open post build shell script and write bash commands for docker image build.**
<img width="842" height="379" alt="jen_6" src="https://github.com/user-attachments/assets/0ebef490-9865-41aa-8026-4fe332e136a5" />
**Once Image is build, now tag and push to Azure container registry.**
<img width="844" height="380" alt="jen_7" src="https://github.com/user-attachments/assets/ec9c2b1c-11db-499b-9435-1f84397e9412" />
<img width="1366" height="611" alt="jen_4" src="https://github.com/user-attachments/assets/e46f8e58-0954-46f8-ba14-5731db90e9f3" />
<img width="1366" height="607" alt="jen_2" src="https://github.com/user-attachments/assets/7d09feec-a45e-4f0e-b54e-eb5430988c98" />
<img width="1366" height="610" alt="jen_3" src="https://github.com/user-attachments/assets/9adc47ab-43e7-42e4-a86b-cee31c455757" />

### **Docker Containerization**

Docker is used to package the application and its runtime dependencies into a portable container image.

Once Image is build we can view our images on docker
<img width="1366" height="403" alt="docker" src="https://github.com/user-attachments/assets/85cf6227-d899-43e4-829f-043d328e7e7f" />

The resulting image is used for deployment to the Kubernetes environment.

### **Azure Container Registry (ACR)**

Azure Container Registry is used as the private container image repository for storing and managing application images.

Implementation activities:

- Creating an Azure Container Registry instance.
- Configuring registry authentication.
- Building the Docker image.
- Tagging the image with the ACR login server.
- Pushing the image to ACR.
- Verifying the image and its tags in the Azure Portal.
  
<img width="1366" height="605" alt="acr_1" src="https://github.com/user-attachments/assets/71b2c77e-9974-4f75-8f50-789fecdf09ab" />
<img width="1366" height="614" alt="acr_2" src="https://github.com/user-attachments/assets/6b0f6fe6-33f0-419b-8752-9299c726704d" />
<img width="1366" height="614" alt="acr_3" src="https://github.com/user-attachments/assets/78eec0fc-47b7-4fe7-b9ba-30f293911049" />
<img width="1366" height="611" alt="acr_4" src="https://github.com/user-attachments/assets/5ac4ae15-f9e0-4371-a62b-ea70276e2240" />
**Once image is pused to ACR we can view the image under repo1 repository in myjavapp**
<img width="1366" height="614" alt="acr_5" src="https://github.com/user-attachments/assets/fab329cc-07c2-49ce-b435-de361d68dd21" />

### **Azure Kubernetes Service (AKS)**

Azure Kubernetes Service is used to deploy and manage the containerized application.

AKS provides a managed Kubernetes environment for application orchestration.

Implementation activities:

- Provisioning the AKS cluster.
- Configuring Kubernetes access using Azure CLI.
- Connecting to the cluster using kubectl.
- Configuring the application deployment.
- Deploying the application image from ACR.
- Verifying application Pods and Deployments.
- Checking the Kubernetes Service configuration.
<img width="1366" height="608" alt="Aks" src="https://github.com/user-attachments/assets/7bb725b3-54fd-4b85-9e11-efd930957fd9" />

Once Connected with Azure Kubernetes service (AKS) CLI. We need to connect our Azure container registry (ACR) with AKS using the commands.

**az acr show --name <ACR_resource_name> --query id --output tsv**

This Azure CLI command retrieves the Azure Container Registry (ACR) resource ID. which we attach to this command below.

**az aks update -n <cluster_name> -g <azure_resource_group_name> --attach-acr <resource_id>**

This gives your AKS cluster permission to pull Docker images from your private Azure Container Registry.

<img width="1366" height="196" alt="mclsd" src="https://github.com/user-attachments/assets/28ce825e-7f48-4e9c-bbc5-91e4d8aa52f4" />

### **Deployment Verification**

After completing the deployment process, Kubernetes resources are inspected to verify the application status.

Expected verification points:

- Kubernetes nodes are in Ready state.
- Application Pods are running successfully.
- Deployment replicas match the configured requirements.
- Kubernetes Service is configured correctly.
- The application is accessible through its configured endpoint, where applicable.

<img width="840" height="164" alt="kube_3" src="https://github.com/user-attachments/assets/0eb151d8-b014-41c4-b545-1193d5a4024e" />
<img width="1354" height="281" alt="kube_1" src="https://github.com/user-attachments/assets/c1fac378-342d-41ac-9f32-efe21f295696" />
<img width="1366" height="117" alt="kube_2" src="https://github.com/user-attachments/assets/8d4f35b1-c9f1-4b66-a5bc-5125a9657a8b" />

### **Application Testing/output**

Application running
<img width="1366" height="444" alt="output" src="https://github.com/user-attachments/assets/93cbd900-5fef-47e2-b645-27dc717cccd0" />

### **Key Learning Outcomes**

Through this project, the following practical concepts were explored:

- Source code management and version control using Git.
- CI/CD automation and build management using Jenkins.
- Container image creation and management using Docker.
- Private container image storage using Azure Container Registry.
- Kubernetes deployment and orchestration using AKS.
- Azure resource management through Azure CLI.
- Application deployment verification and troubleshooting.
- Integration of multiple DevOps tools into a single workflow.

### **Conclusion**

This project demonstrates the integration of commonly used DevOps tools and Microsoft Azure services to establish an automated application delivery workflow.

By combining Git, Jenkins, Docker, Azure Container Registry, and Azure Kubernetes Service, the project provides practical exposure to source code management, CI/CD automation, containerization, cloud infrastructure, and Kubernetes-based application deployment.

The implementation serves as a foundation for understanding real-world DevOps workflows and further exploring cloud-native technologies, infrastructure automation, monitoring, and deployment optimization.











