<div align="center">

# **Design and Implementation of Docker Container Architecture on Microsoft Azure**

</div>


## 📚 **Table of Contents**
- [Scenario](#scenario)
- [Architecture Diagram](#architecture-diagram)
- [Objective](#objective)
- [Implementation Visuals](#Implementation-Visuals)
- [Clean-up](#clean-up)
  - [Step-1: Delete MFA for IAM-User-1](#step-1--delete-mfa-for-iam-user-1)
  - [Step-2: Login without MFA — Only list buckets, no access to bucket 1992](#step-2--after-deleting-mfa-for-iam-user-1-if-he-login-he-can-only-list-the-bucket-but-not-access-specific-bucket-1992-with-object)
- [Conclusion](#conclusion)

## Scenario

- An Azure resource group, virtual network, subnet, and network security group are created to prepare the cloud environment.
- An Azure virtual machine with a public IP is deployed and HTTP traffic on port 80 is allowed through NSG.
- Docker Engine is installed on the virtual machine to enable container execution.
- The Nginx image is pulled from Docker Hub and run as a container inside the virtual machine.
- The client accesses the application using the VM public IP and the Nginx web page is displayed successfully.

 ## Architecture Diagram

  ![image.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/image_kGEYCCzuo7NqolmvkK7Zu.png?ixlib=js-3.8.0 "image.png")
 ### Architecture Flow
 1. A **Virtual Machine** is created in Azure under a **Resource Group**.
 2. A **Virtual Network (VNet)** and **Subnet** are configured for network isolation.
 3. A **Network Security Group (NSG)** allows **HTTP traffic on port 80**.
 4. **Docker Engine** is manually installed on the Azure VM.
 5. The VM pulls the **Nginx image (nginx:1.17.0)** from **Docker Hub**.
 6. The Nginx container is started and listens on **port 80**.
 7. The **client accesses the application** using the VM’s public IP.

## **Objective**

To demonstrates Docker containerization on Microsoft Azure using Docker Hub, Azure Container Registry (ACR), and an Azure VM running Docker Engine with Nginx.

The application is containerized, stored in registries, and deployed inside an Azure Virtual Machine.

## Implementation Visuals 

### Step 1: Azure Portal Home Page

![Screenshot 2026-01-09 192247.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192247_w2YCda1ewjQs_mx0eawH7.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192247.png")

### Step 2: Searching for Virtual Machines

![Screenshot 2026-01-09 192714.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192714_euSpGTKVV7myWalggv_-w.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192714.png")

### Step 3: Virtual Machines Service Page

![Screenshot 2026-01-09 192745.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192745_wWPr7TKAZWUngkoDvE6nZ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192745.png")

### Step 4: Initiating Virtual Machine Creation

![Screenshot 2026-01-09 192806.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192806_AeQSRKPQLLDGZkXlZBIoJ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192806.png")

### Step 5: Resource Group Creation

![Screenshot 2026-01-09 192951.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192951_jfjBF_lyQc-XpJogPCJbF.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192951.png")

### Step 6: Basic Virtual Machine Configuration

![Screenshot 2026-01-09 193027.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193027_UqYyj_NQVBsKn8-ZFVn6Y.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193027.png")

### Step 7: Virtual Machine Size and Administrator Setup

![Screenshot 2026-01-09 193319.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193319_wKwii2pgdQQ_zP5X62TAq.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193319.png")

### Step 8: 
![Screenshot 2026-01-09 193827.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193827_yl2lmaObKlkijQLLmtojW.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193827.png")

### Step 9: Network and Inbound Port Configuration

![Screenshot 2026-01-09 193851.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193851_PUl71ONMk3BJl7rngvp2I.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193851.png")

### Step 10: Disk Configuration

![Screenshot 2026-01-09 193957.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193957_C7F2dxBejAJTbWQFTlSul.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193957.png")






