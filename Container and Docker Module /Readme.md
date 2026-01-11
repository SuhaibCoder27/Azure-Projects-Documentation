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

### Deployment of NGINX Web Server Using Azure Container Instances

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

### Azure Linux Virtual Machine Setup with Dockerized Web Server

</div>

---

## Step 1: Search for Container Instance Service

<img width="1647" height="842" alt="Screenshot 2026-01-09 213731" src="https://github.com/user-attachments/assets/26390c8b-bfe0-4471-ae2f-7ada70dda467" />

## Step 2: Creating Azure Container Instances

<img width="1671" height="851" alt="image" src="https://github.com/user-attachments/assets/d4946369-90e4-44bf-b1a5-b83bfdb3cf6c" />

## Step 3: Open Container Instance Page

<img width="1643" height="861" alt="Screenshot 2026-01-09 213816" src="https://github.com/user-attachments/assets/7e1e0dd9-8aea-41c0-858c-7cac03638b09" />

## Step 4: Enter Container Basic Details

<img width="1656" height="865" alt="Screenshot 2026-01-09 213925" src="https://github.com/user-attachments/assets/db32f3ea-273a-47de-a42d-97690eb022a4" />

## Step 4: Choose Image Source and Image

<img width="1661" height="858" alt="Screenshot 2026-01-09 214020" src="https://github.com/user-attachments/assets/2981eb0d-33fc-4231-9ca8-e98e6a100f3a" />

## Step 5:

<img width="1535" height="862" alt="Screenshot 2026-01-09 214431" src="https://github.com/user-attachments/assets/8d85b7fc-0a36-4fbc-b10a-189be6445860" />

## Step 6:

<img width="1658" height="866" alt="Screenshot 2026-01-09 214514" src="https://github.com/user-attachments/assets/a0bb82c3-c020-4d8c-af92-4a597e1259d3" />

## Step 7:

<img width="1238" height="157" alt="Screenshot 2026-01-09 214548" src="https://github.com/user-attachments/assets/6b5bc253-8015-48ac-8c67-fa8ef21206b3" />

## Step 8:

<img width="1474" height="532" alt="Screenshot 2026-01-09 214614" src="https://github.com/user-attachments/assets/480543c7-9b9a-4699-b590-cb5c1bac502a" />







