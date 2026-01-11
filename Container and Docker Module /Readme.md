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

<div align="center">

### Azure Linux Virtual Machine Setup with Dockerized Web Server

</div>

---

### Step 1: Azure Portal Home Page

![Screenshot 2026-01-09 192247.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192247_w2YCda1ewjQs_mx0eawH7.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192247.png")

### Step 2: Searching for Virtual Machines

![Screenshot 2026-01-09 192714.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192714_euSpGTKVV7myWalggv_-w.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192714.png")

### Step 3: Virtual Machines Service Page

![Screenshot 2026-01-09 192745.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192745_wWPr7TKAZWUngkoDvE6nZ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192745.png")

### Step 4: Initiating Virtual Machine Creation

![Screenshot 2026-01-09 192806.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192806_AeQSRKPQLLDGZkXlZBIoJ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192806.png")

### Step 5: Open Virtual machine Creation 

![Screenshot 2026-01-09 192951.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20192951_jfjBF_lyQc-XpJogPCJbF.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 192951.png")

### Step 6: Resource Group Creation 

![Screenshot 2026-01-09 193027.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193027_UqYyj_NQVBsKn8-ZFVn6Y.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193027.png")

### Step 7: Basic Virtual Machine Configuration 

![Screenshot 2026-01-09 193319.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193319_wKwii2pgdQQ_zP5X62TAq.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193319.png")

### Step 8: Administrator account Setup 
![Screenshot 2026-01-09 193827.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193827_yl2lmaObKlkijQLLmtojW.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193827.png")

### Step 9: Network and Inbound Port Configuration

![Screenshot 2026-01-09 193851.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193851_PUl71ONMk3BJl7rngvp2I.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193851.png")

### Step 10: Disk Configuration

![Screenshot 2026-01-09 193957.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20193957_C7F2dxBejAJTbWQFTlSul.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 193957.png")

### step 11: Networking Configuration 

![Screenshot 2026-01-09 194359.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194359_JDgqlXPsLE5wn2vA1P4wp.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194359.png")

### Step 12: Review and Create – Validation Passed

![Screenshot 2026-01-09 194442.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194442_42QIsJooqWQ1WzujNq4Nb.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194442.png")

### Step 13: Virtual Machine Deployment Completion

![Screenshot 2026-01-09 194609.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194609_yox8BvZm0D0E9DnuHbfS0.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194609.png")

### Step 14: Accessing the Virtual Machine Resource

![Screenshot 2026-01-09 194631.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194631_zNya3FEvzmGtZmnYlPWmV.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194631.png")

### Step 15: Searching for Network Security Groups (NSG)

![Screenshot 2026-01-09 194734.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194734_fSkah5wZ8S8iEGtzwXtUn.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194734.png")

### Step 16: Network Security Group Listing

![Screenshot 2026-01-09 194744.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20194744_sSOlSi4Sfg1H0Qr0wqRRl.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 194744.png")

### Step 17: Viewing Network Interfaces Details

![Screenshot 2026-01-09 195030.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195030_FQW4H81nA1mp3GzHptXX9.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195030.png")

### Step 18: Disassociating Network Interface from NSG

![Screenshot 2026-01-09 195229.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195229_2dxEpB0Pqz4NLYITKgRXx.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195229.png")

### Step 19: Successful Network Interface Disassociation

![Screenshot 2026-01-09 195248.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195248_HIZzexQjFUc-5c4AYtbRZ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195248.png")

### Step 20: Network Security Group – Subnets View (No Association)

![Screenshot 2026-01-09 195300.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195300_xskLZgw8lt8ROdeiKneYu.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195300.png")

### Step 22: Associating the NSG with a Virtual Network Subnet

![Screenshot 2026-01-09 195331.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195331_SUfLoe7klotsObOmf-DqM.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195331.png")

### Step 23: Subnet Successfully Associated with NSG

![Screenshot 2026-01-09 195412.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195412_UkxqmJMx5mMIV2zP09NIV.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195412.png")

### Step 24: Viewing Virtual Machines in Azure Portal To check nsg is binded

![Screenshot 2026-01-09 195936.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195936_h50n7GqkhsvXVDTrg_X6o.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195936.png")

### Step 25: Launching PuTTY from Local Machine

![Screenshot 2026-01-09 200024.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200024_Y8X8AKIXRBY_IfXXGINgT.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200024.png")

### Step 26: Configuring PuTTY for SSH Connection

![Screenshot 2026-01-09 200113.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200113_Aofn_3i7fiD8SGCHG1j2Q.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200113.png")

### Step 27: PuTTY Security Alert – Host Key Verification

![Screenshot 2026-01-09 200126.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200126_PnLfaJxFPtSn6BbW7dGDm.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200126.png")

### Step 28: Successful Login to Ubuntu Virtual Machine

![Screenshot 2026-01-09 200137.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200137_G5-6DCrN-MW1-RSiAj86H.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200137.png")

![Screenshot 2026-01-09 200242.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200242_VIdNZz7jVCQCoemJ_byM2.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200242.png")

![Screenshot 2026-01-09 200708.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200708_ck4Aa0oBXB1MKDn7yYZGw.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200708.png")

![Screenshot 2026-01-09 200748.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200748_QhAeYCPtJFdL1w6y0BJln.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200748.png")

![Screenshot 2026-01-09 201441.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201441_2AGUrmWujpy6qhHwynpGz.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201441.png")

![Screenshot 2026-01-09 201644.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201644_72dGeGG8fHyX5nr3Zbi1u.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201644.png")

![Screenshot 2026-01-09 201714.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201714_sez7uCpQFtFYcMBXhfpAB.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201714.png")

![Screenshot 2026-01-09 201740.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201740_t7P7oyC91NCGYNHi_Id32.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201740.png")

![Screenshot 2026-01-09 201802.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201802_RA4ige28Ozlqq2c4OuhpK.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201802.png")

![Screenshot 2026-01-09 201846.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201846_cma782W3ksDOl5HDjfmmp.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201846.png")

![Screenshot 2026-01-09 201923.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201923_RWxmi3CwZLgU9_KXvK83C.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201923.png")

![Screenshot 2026-01-09 201942.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20201942_6ai-XLpl44zrjMXjq_Poa.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 201942.png")

## Linux Prompt 

// Update the package index
-- sudo apt-get update

// Install packages to allow apt to use the repository over HTTPS
sudo apt install apt-transport-https ca-certificates curl software-properties-common

// Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

// Setup a stable repository
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

// Update the package index
sudo apt-get update

// Install docker, containerd
sudo apt-get install docker-ce

// Pull the nginx image
sudo docker pull nginx:1.17.0

// Create a container out of the image
sudo docker run --name sampleapp -p 80:80 -d nginx:1.17.0

### Step 29: Entering the Virtual Machine Public IP Address in Browser

<img width="1581" height="244" alt="Screenshot 2026-01-09 202117" src="https://github.com/user-attachments/assets/682e695a-6666-44d6-927e-967f8bb22187" />

### Step 30: NGINX Default Web Page Successfully Displayed

<img width="1622" height="783" alt="Screenshot 2026-01-09 202134" src="https://github.com/user-attachments/assets/f24e7c6b-0205-43fe-8e66-68444ac77d99" />

---

<div align="center">

## Deployment of NGINX Web Server Using Azure Container Instances using Quickstart Image

</div>

---

## Step 1: Azure Portal Home Page

![Screenshot 2026-01-09 212852.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20212852_TNeMATRdxAFBhPepQ4tWJ.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 212852.png")

## Step 2: Searching for Container Instance Service

![Screenshot 2026-01-09 212953.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20212953_QRxjr9e5zIyG_PNV0QDFC.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 212953.png")

## Step 3: Creating Azure Container Instances

<img width="1671" height="851" alt="image" src="https://github.com/user-attachments/assets/d4946369-90e4-44bf-b1a5-b83bfdb3cf6c" />

## Step 4: Configuring Basic Container Details

![Screenshot 2026-01-09 213159.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213159_YLQIpeLXDjf4hYWYdoc3S.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213159.png")

## Step 5: Selecting Container Image

![Screenshot 2026-01-09 213227.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213227_X6HZ3E345-AS4W3Ql7lz6.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213227.png")

## Step 6: Reviewing Container Configuration

![Screenshot 2026-01-09 213309.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213309_lmBVaHR-piXCn_mad9jXs.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213309.png")


## Step 7: Container Deployment Completion

![Screenshot 2026-01-09 213505.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213505_NSOWY0PbLRwRVQ05zmDGz.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213505.png")

## Step 8: Accessing the Container Resource

![Screenshot 2026-01-09 213527.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213527_lbwa3lRwqjRP06Mv9HUQ6.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213527.png")

## Step 9: Accessing the Containerized NGINX Application Using Public IP

![Screenshot 2026-01-09 213555.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213555_ZaKArWCZdcbpnqPNQopT5.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213555.png")

## Step 10: NGINX Default Web Page Successfully Displayed

![Screenshot 2026-01-09 213612.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20213612_iA5nv7BNnmQym7pItQw1O.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 213612.png")

---

<div align="center">

## Deployment of NGINX Web Server Using Azure Container Instances using Other Registry

</div>

---

## Step 1: Search for Container Instance Service

<img width="1647" height="842" alt="Screenshot 2026-01-09 213731" src="https://github.com/user-attachments/assets/26390c8b-bfe0-4471-ae2f-7ada70dda467" />

## Step 2: Creating Azure Container Instances

<img width="1671" height="851" alt="image" src="https://github.com/user-attachments/assets/d4946369-90e4-44bf-b1a5-b83bfdb3cf6c" />

## Step 3: Open and Enter Container Basic Details

<img width="1643" height="861" alt="Screenshot 2026-01-09 213816" src="https://github.com/user-attachments/assets/7e1e0dd9-8aea-41c0-858c-7cac03638b09" />

## Step 4: Choose Image Source and Image

<img width="1656" height="865" alt="Screenshot 2026-01-09 213925" src="https://github.com/user-attachments/assets/db32f3ea-273a-47de-a42d-97690eb022a4" />

## Step 5: Review Container Configuration

<img width="1661" height="858" alt="Screenshot 2026-01-09 214020" src="https://github.com/user-attachments/assets/2981eb0d-33fc-4231-9ca8-e98e6a100f3a" />

## Step 6: Deployment Completion Confirmation

<img width="1535" height="862" alt="Screenshot 2026-01-09 214431" src="https://github.com/user-attachments/assets/8d85b7fc-0a36-4fbc-b10a-189be6445860" />

## Step 7: Accessing the Container Resource

<img width="1658" height="866" alt="Screenshot 2026-01-09 214514" src="https://github.com/user-attachments/assets/a0bb82c3-c020-4d8c-af92-4a597e1259d3" />

## Step 8: Access Container Resources via Public IP in Web Browser

<img width="1238" height="157" alt="Screenshot 2026-01-09 214548" src="https://github.com/user-attachments/assets/6b5bc253-8015-48ac-8c67-fa8ef21206b3" />

## Step 9: Verify NGINX Web Server

<img width="1474" height="532" alt="Screenshot 2026-01-09 214614" src="https://github.com/user-attachments/assets/480543c7-9b9a-4699-b590-cb5c1bac502a" />

---

<div align="center">

## Deployment of NGINX Web Server Using Azure Container Instances using Other Registry

</div>

---
## Step 1: open github repository 

<img width="1192" height="167" alt="Screenshot 2026-01-09 214838" src="https://github.com/user-attachments/assets/d1076718-15ad-4dc8-8226-6c964f765610" />

## Step 2: Review Repository Structure

<img width="1319" height="690" alt="Screenshot 2026-01-09 214931" src="https://github.com/user-attachments/assets/09733f43-c9f2-49f4-9d73-5c5c7ba98cae" />

## Step 3: View Application Source Code

<img width="1889" height="851" alt="Screenshot 2026-01-09 215409" src="https://github.com/user-attachments/assets/566178a7-3cda-41d9-87ed-01986a5b1eef" />

## Step 4: Open microsoft azure and launch cloud shell

<img width="1662" height="868" alt="Screenshot 2026-01-09 215513" src="https://github.com/user-attachments/assets/e042f594-6980-4f72-af42-8e3bcf8ae161" />

## Step 5: Clone the GitHub Repository

<img width="1236" height="107" alt="Screenshot 2026-01-09 215708" src="https://github.com/user-attachments/assets/f5c60517-c46c-4d73-9e2f-4fa274b28ba8" />

## Step 6: Verify Repository Download

<img width="1469" height="321" alt="Screenshot 2026-01-09 215826" src="https://github.com/user-attachments/assets/f48e9f44-a8e6-4cca-9c25-5a2ae79e5ee0" />

## Step 7: Navigate into the Project Directory

<img width="1464" height="324" alt="Screenshot 2026-01-09 215924" src="https://github.com/user-attachments/assets/fef066ef-ef3d-46e8-81fa-72232f2fac2e" />

## Step 8: Open Project in Code Editor

<img width="1249" height="181" alt="Screenshot 2026-01-09 220152" src="https://github.com/user-attachments/assets/69ebd349-acd7-4f7b-ac52-8410c8858bdb" />

## Step 9: Inspect Application Files

<img width="1595" height="325" alt="Screenshot 2026-01-09 220456" src="https://github.com/user-attachments/assets/d5976544-9c1d-47cc-a102-90cf19b2d305" />

## Step 10: Confirm Containerized Application Readiness

<img width="1865" height="321" alt="Screenshot 2026-01-09 220700" src="https://github.com/user-attachments/assets/198ad78e-60ee-41dc-90ac-1ad4800dc7e5" />

<img width="1919" height="322" alt="Screenshot 2026-01-09 220857" src="https://github.com/user-attachments/assets/ba7c0e7d-abdf-40b5-ae64-ef0607135b30" />

<img width="1590" height="664" alt="Screenshot 2026-01-09 221038" src="https://github.com/user-attachments/assets/26e982f6-efb1-4958-a40c-79fd955e9e0d" />

<img width="1654" height="815" alt="Screenshot 2026-01-09 221102" src="https://github.com/user-attachments/assets/4148d200-1f52-401b-8c2c-d03bc35bfb0b" />

<img width="1538" height="863" alt="Screenshot 2026-01-09 221309" src="https://github.com/user-attachments/assets/27491696-b515-4476-ac60-0095c8a5a649" />

<img width="1401" height="859" alt="Screenshot 2026-01-09 221354" src="https://github.com/user-attachments/assets/3b53dd92-9afb-422e-8d3c-2984fb0d0fb1" />

<img width="1442" height="853" alt="Screenshot 2026-01-09 221451" src="https://github.com/user-attachments/assets/2c908ecb-8cd0-466a-ad4c-b0b761e76b88" />

<img width="1662" height="244" alt="Screenshot 2026-01-09 221734" src="https://github.com/user-attachments/assets/b145014e-682a-4055-8028-36c051370f67" />

<img width="1651" height="216" alt="Screenshot 2026-01-09 221813" src="https://github.com/user-attachments/assets/6caa9b18-62e6-474d-b4d9-062758173c1b" />

<img width="1305" height="319" alt="Screenshot 2026-01-09 222704" src="https://github.com/user-attachments/assets/d7c9b14e-acd0-4ba3-8634-e4c22a0b21eb" />

<img width="1413" height="320" alt="Screenshot 2026-01-09 222740" src="https://github.com/user-attachments/assets/f5efc4e2-0461-4325-aadb-12f756351f0d" />

<img width="801" height="318" alt="Screenshot 2026-01-09 222813" src="https://github.com/user-attachments/assets/e3c92f78-089a-42a1-a517-0254ea39915a" />

<img width="848" height="314" alt="Screenshot 2026-01-09 222918" src="https://github.com/user-attachments/assets/e79b2ee0-3e6f-4559-a314-43d63e543b20" />

<img width="1651" height="865" alt="Screenshot 2026-01-09 223037" src="https://github.com/user-attachments/assets/95c8d274-58be-4095-b5cb-0502a089d199" />

<img width="1660" height="853" alt="Screenshot 2026-01-09 223102" src="https://github.com/user-attachments/assets/1f812dff-a13a-4a65-95cb-a17252ac0e8d" />

<img width="1658" height="852" alt="Screenshot 2026-01-09 223219" src="https://github.com/user-attachments/assets/daea4293-10fc-4c4f-8dee-e8b545ce89dc" />

<img width="1652" height="866" alt="Screenshot 2026-01-09 223612" src="https://github.com/user-attachments/assets/1abc9ae0-6548-40d5-b21f-1c7b463762c7" />

<img width="1664" height="862" alt="Screenshot 2026-01-09 223645" src="https://github.com/user-attachments/assets/0c4f23e5-90d4-45f7-ada7-f577e725e20f" />

<img width="1460" height="863" alt="Screenshot 2026-01-09 223734" src="https://github.com/user-attachments/assets/28d2a603-e67e-4fd2-90a4-280e0efb2a7d" />

<img width="1459" height="858" alt="Screenshot 2026-01-09 223902" src="https://github.com/user-attachments/assets/9e7fe542-1ebb-4d06-ab23-dd6c0fd167af" />

<img width="1661" height="662" alt="Screenshot 2026-01-09 223936" src="https://github.com/user-attachments/assets/30538569-5767-48cc-b6c6-076ce99a4154" />

<img width="1649" height="796" alt="Screenshot 2026-01-09 224008" src="https://github.com/user-attachments/assets/47061707-0775-4780-bef5-020c7e877f18" />

<img width="1647" height="857" alt="Screenshot 2026-01-09 224033" src="https://github.com/user-attachments/assets/6ba98677-743a-49c8-ac2b-4dc2f6fe13cd" />

<img width="1663" height="844" alt="Screenshot 2026-01-09 224142" src="https://github.com/user-attachments/assets/b8fb1746-c8bb-439b-a8ca-15ede4293482" />

<img width="1676" height="868" alt="Screenshot 2026-01-09 224200" src="https://github.com/user-attachments/assets/77bb868c-bef6-4c0e-84bf-ac0781796121" />

<img width="1643" height="795" alt="Screenshot 2026-01-09 224228" src="https://github.com/user-attachments/assets/cea9fd5b-45a3-4b2c-b7ae-264555eda3f2" />

<img width="1661" height="829" alt="Screenshot 2026-01-09 224248" src="https://github.com/user-attachments/assets/27bdab5f-9e00-47ed-a4d1-f63793aca3ce" />

<img width="1247" height="856" alt="Screenshot 2026-01-09 224328" src="https://github.com/user-attachments/assets/a0107ed8-3ad2-4a0f-b7b3-25c2c4ee0a0a" />

<img width="1245" height="866" alt="Screenshot 2026-01-09 224434" src="https://github.com/user-attachments/assets/2f8f89a2-d6a5-47f2-845f-773ac35db981" />

<img width="1388" height="865" alt="Screenshot 2026-01-09 224507" src="https://github.com/user-attachments/assets/0d6f230d-c31f-4a0b-b8fb-3ec434a883c3" />

<img width="1663" height="693" alt="Screenshot 2026-01-09 224644" src="https://github.com/user-attachments/assets/cc8313b9-a9ab-4643-8c93-03256d551394" />

<img width="1638" height="831" alt="Screenshot 2026-01-09 224715" src="https://github.com/user-attachments/assets/60e1a3ef-8833-4f55-b213-7c730657612a" />

<img width="1133" height="163" alt="Screenshot 2026-01-09 224740" src="https://github.com/user-attachments/assets/a50726e4-49d4-4bf9-a7ca-df26743cfcfc" />

<img width="1660" height="944" alt="Screenshot 2026-01-09 224805" src="https://github.com/user-attachments/assets/55c7d41b-475f-446f-8d90-2c269235a1ec" />

<img width="1648" height="860" alt="Screenshot 2026-01-09 224857" src="https://github.com/user-attachments/assets/43df290a-ffd0-4769-a439-52565bf3f743" />

<img width="1662" height="799" alt="Screenshot 2026-01-09 224933" src="https://github.com/user-attachments/assets/2cd50fa4-54a4-43be-b03d-7292dd678028" />

<img width="1660" height="791" alt="Screenshot 2026-01-09 225002" src="https://github.com/user-attachments/assets/9f67b530-f9ff-4cb1-ba7a-401052c86bfb" />

<img width="1913" height="818" alt="Screenshot 2026-01-09 225112" src="https://github.com/user-attachments/assets/4b176ae3-3fa3-4d27-9b28-aa4be9d75958" />

<img width="1915" height="813" alt="Screenshot 2026-01-09 225152" src="https://github.com/user-attachments/assets/101d69cc-e37a-4ab0-97cb-a93a0f344d53" />

<img width="1662" height="647" alt="Screenshot 2026-01-09 225250" src="https://github.com/user-attachments/assets/f8d131b5-7883-40fa-819a-004d692be271" />

<img width="1916" height="815" alt="Screenshot 2026-01-09 225317" src="https://github.com/user-attachments/assets/8a296092-6d79-4b2b-a3fd-c296880e004d" />

<img width="1917" height="811" alt="Screenshot 2026-01-09 225341" src="https://github.com/user-attachments/assets/e57e7460-f3f1-4d78-aa78-debdea83cc74" />

<img width="1918" height="819" alt="Screenshot 2026-01-09 225422" src="https://github.com/user-attachments/assets/6914e2ce-1843-43f8-9067-93237463f750" />

<img width="1919" height="815" alt="Screenshot 2026-01-09 225455" src="https://github.com/user-attachments/assets/29908f74-eb9d-443a-a2b5-76f3f22ee0df" />

<img width="1892" height="819" alt="Screenshot 2026-01-09 225657" src="https://github.com/user-attachments/assets/ec5b0148-f22f-4c93-956f-159288bea464" />

