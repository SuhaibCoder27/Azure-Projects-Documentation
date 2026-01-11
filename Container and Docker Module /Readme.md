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

### Step 20: 

![Screenshot 2026-01-09 195300.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195300_xskLZgw8lt8ROdeiKneYu.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195300.png")

### Step 22: 

![Screenshot 2026-01-09 195331.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195331_SUfLoe7klotsObOmf-DqM.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195331.png")

### Step 23: 

![Screenshot 2026-01-09 195412.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195412_UkxqmJMx5mMIV2zP09NIV.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195412.png")

### Step 24: 

![Screenshot 2026-01-09 195936.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20195936_h50n7GqkhsvXVDTrg_X6o.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 195936.png")

### Step 25: 

![Screenshot 2026-01-09 200113.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200113_Aofn_3i7fiD8SGCHG1j2Q.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200113.png")

### Step 26: 

![Screenshot 2026-01-09 200024.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200024_Y8X8AKIXRBY_IfXXGINgT.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200024.png")

### Step 27: 

![Screenshot 2026-01-09 200137.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200137_G5-6DCrN-MW1-RSiAj86H.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200137.png")

### Step 28: 

![Screenshot 2026-01-09 200126.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200126_PnLfaJxFPtSn6BbW7dGDm.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200126.png")

### Step 29: 

![Screenshot 2026-01-09 200242.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200242_DhWK7vNtmslp5cKxfPsxh.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200242.png")

### Step 30: 

![Screenshot 2026-01-09 200708.png](https://eraser.imgix.net/workspaces/XY7MeNC8cFGVxzWvYyWu/h28iw3vmmaTZF0WlsYaXTHBzHD63/Screenshot%202026-01-09%20200708_IXIssPM0vG_nXKXVtg_Tb.png?ixlib=js-3.8.0 "Screenshot 2026-01-09 200708.png")


















