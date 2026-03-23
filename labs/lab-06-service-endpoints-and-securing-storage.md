# 🌐🔐 Lab 06: Service Endpoints and Securing Storage

### CCSP Domain:

#### ☁️ D1. Cloud Concepts, Architecture and Design

#### 🔑 D2. Cloud Data Security 

---

## 📚 Lab Navigation

### 🔎 Overview

---

## 📚 Lab Navigation

### 🔎 Overview

* [Lab Scenario](#lab-scenario)
* [Lab Objectives](#lab-objectives)
* [Architecture Diagram](service-endpoints-and-securing-storage-diagram)
* [Task 1: Create a Virtual Network](#task-1-create-a-virtual-network)
* [Task 2: Add Subnet and Configure Service Endpoint](#task-2-add-a-subnet-to-the-virtual-network-and-configure-a-storage-endpoint)
* [Task 3: Configure NSG for Private Subnet](#task-3-configure-a-network-security-group-to-restrict-access-to-the-subnet)
* [Task 4: Configure NSG for Public Subnet](#task-4-configure-a-network-security-group-to-allow-rdp-on-the-public-subnet)
* [Task 5: Create Storage Account and File Share](#task-5-create-a-storage-account-with-a-file-share)
* [Task 6: Deploy Virtual Machines](#task-6-deploy-virtual-machines-into-the-designated-subnets)
* [Task 7: Test Access from Private Subnet (Allowed)](#task-7-test-the-storage-connection-from-the-private-subnet-to-confirm-that-access-is-allowed)
* [Task 8: Test Access from Public Subnet (Denied)](#task-8-test-the-storage-connection-from-the-public-subnet-to-confirm-that-access-is-denied)
* [Clean Up Resources](#clean-up-resources)
* [Lessons Learned](#lessons-learned)



# Lab Scenario

You have been asked to create a proof of concept to demonstrate securing Azure file shares. Specifically, you want to:

* Create a **storage endpoint** so traffic stays within the Azure backbone.
* Configure the endpoint so **only resources from a specific subnet** can access the storage.
* Confirm that resources **outside** of that subnet are blocked.

> ⚠️ All resources in this lab use the **East US** region. Verify with your instructor before proceeding.

---

# Lab Objectives

In this lab, you will complete **Exercise 1: Service endpoints and security storage**.

### Service Endpoints and Securing Storage Diagram


![Azure Container Register and Kubernetes Cluster](../labs/lab-06-media/service-endpoints-and-securing-storage-diagram.png)


![All Resources](../labs/lab-06-media/all-resources.png)
---

# Exercise 1: Service endpoints and security storage

**Estimated timing: 45 minutes**

---

## Task 1: Create a virtual network

In this task, you will create the foundation for your lab infrastructure.

1. Sign-in to the [Azure portal](https://portal.azure.com/).
2. Search for **Virtual networks** and click **+ Create**.
3. On the **Basics** tab, use these settings:

| Setting | Value |
| --- | --- |
| Subscription | Your active subscription |
| Resource group | **AZ500LAB12** (Create New) |
| Name | **myVirtualNetwork** |
| Region | **East US** |

4. On the **IP addresses** tab, set address space to `10.0.0.0/16`.
5. Edit the **default** subnet:
* **Name:** `Public`
* **Range:** `10.0.0.0/24`





6. Click **Review + create**, then **Create**.


![Create Network](../labs/lab-06-media/create-network-1.png)

![Create Network](../labs/lab-06-media/create-network-2.png)

![Create Network](../labs/lab-06-media/create-network-3.png)

---

## Task 2: Add a subnet to the virtual network and configure a storage endpoint

1. Navigate to **myVirtualNetwork** > **Settings** > **Subnets**.
2. Click **+ Subnet** and specify:

| Setting | Value |
| --- | --- |
| Subnet name | **Private** |
| Subnet address range | **10.0.1.0/24** |
| Service endpoints | **None** (We will enable this via the storage account later) |

3. Click **Add**.

![Create Private Subnet](../labs/lab-06-media/create-private-subnet.png)

![Overall Subnets](../labs/lab-06-media/subnets.png)

---

## Task 3: Configure a network security group to restrict access to the subnet

1. Search for **Network security groups** and click **+ Create**.
2. Name it **myNsgPrivate** in resource group **AZ500LAB12**.
3. Navigate to **Outbound security rules** and click **+ Add**:

| Rule Type | Priority | Name | Port | Destination | Action |
| --- | --- | --- | --- | --- | --- |
| **Allow** | 1000 | Allow-Storage-All | * | Service Tag: **Storage** | Allow |
| **Deny** | 1100 | Deny-Internet-All | * | Service Tag: **Internet** | Deny |



![Create Outbound Rule NSG Private - Allow Storage All](../labs/lab-06-media/private-nsg-outbound-rule-allow-storage-all.png)

![Create Outbound Rule NSG Private - Deny Internet All](../labs/lab-06-media/private-nsg-outbound-rule-deny-internet-all.png)

![Create Outbound Rule NSG Private - Overview](../labs/lab-06-media/private-nsg-outbound-rule-overview.png)

4. Navigate to **Inbound security rules** and click **+ Add**:
* **Name:** `Allow-RDP-All`
* **Destination Port:** `3389`
* **Action:** `Allow` (Priority 1200)


![Create Inbound Rule NSG Private](../labs/lab-06-media/private-nsg-inbound-rule-allow-rdp-all.png)


![Inbound Rule NSG Private - Overview](../labs/lab-06-media/private-nsg-inbound-rule-overview.png)

5. Go to **Subnets** > **Associate** and link it to **myVirtualNetwork / Private**.

![Associate NSG Private Subnet](../labs/lab-06-media/associate-private-subnet-to-nsg.png)


---

## Task 4: Configure a network security group to allow rdp on the public subnet

1. Create a new NSG named **myNsgPublic**.
2. Add an **Inbound security rule**:
* **Destination Port:** `3389`
* **Action:** `Allow`
* **Name:** `Allow-RDP-All`



![Create Inbound Rule NSG Public](../labs/lab-06-media/public-nsg-inbound-rule-allow-rdp-all.png)

![Inbound Rule NSG Public - Overview](../labs/lab-06-media/public-nsg-inbound-rule-overview.png)


3. Associate this NSG with the **Public** subnet.

![Associate NSG Public Subnet](../labs/lab-06-media/associate-public-subnet-to-nsg.png)

---

## Task 5: Create a storage account with a file share

1. Create a **Storage Account** with these settings:
* **Name:** (Globally Unique)
* **Performance:** Standard
* **Redundancy:** LRS

![Create Storage Account](../labs/lab-06-media/create-storage-account.png)

2. Once created, go to **Data storage** > **File Shares** > **+ File Share**.
* **Name:** `my-file-share`
* **Note:** Untick "Enable backup".


3. **Important:** Click **Connect** on the file share, select **Windows**, and copy the PowerShell script. **Save this script for Task 7.**
4. Go to **Security + networking** > **Networking**:
* Select **Enable from selected networks**.
* Click **+ Add existing virtual network**.
* Select **myVirtualNetwork** and the **Private** subnet.


5. Click **Save**.


![Create my-file-share](../labs/lab-06-media/my-file-share.png)

---

## Task 6: Deploy virtual machines into the designated subnets

Create two Windows Server 2022 VMs with **Standard HDD** disks and **no** public inbound ports (the NSG handles this).

| VM Name | Subnet | Public IP |
| --- | --- | --- |
| **myVmPrivate** | Private | (new) |
| **myVmPublic** | Public | (new) |

#### myVmPrivate
![Create myVmPrivate](../labs/lab-06-media/create-private-vm-1.png)
![Create myVmPrivate](../labs/lab-06-media/create-private-vm-2.png)
![Create myVmPrivate](../labs/lab-06-media/create-private-vm-3.png)

#### myVmPublic
![Create myVmPublic](../labs/lab-06-media/create-public-vm-1.png)

---

## Task 7: Test the storage connection from the private subnet to confirm that access is allowed

1. RDP into **myVmPrivate**.
2. Open **PowerShell ISE** and run the script you saved in Task 5.
3. **Expected Result:** The Z: drive maps successfully.
4. Run `Test-NetConnection -ComputerName www.bing.com -Port 80`.
5. **Expected Result:** Connection **fails** (due to the Deny-Internet NSG rule).

![Connect to myVmPrivate](../labs/lab-06-media/connect-private-vm.png)
![Connect myVmPrivate to my-file-share](../labs/lab-06-media/connect-private-vm-to-my-file-share-1.png)
![Connect myVmPrivate to my-file-share](../labs/lab-06-media/connect-private-vm-to-my-file-share-2.png)
![Connect myVmPrivate to my-file-share](../labs/lab-06-media/connect-private-vm-to-my-file-share-3.png)

![Connect myVmPrivate to Bing](../labs/lab-06-media/connect-private-vm-4-internet-ping.png)


---

## Task 8: Test the storage connection from the public subnet to confirm that access is denied

1. RDP into **myVmPublic**.
2. Run the same PowerShell storage script.
3. **Expected Result:** `New-PSDrive : Access is denied`. This is because the Public subnet is not authorized on the storage account firewall.
4. Run `Test-NetConnection -ComputerName www.bing.com -Port 80`.
5. **Expected Result:** Connection **succeeds**.

![Connect myVmPublic to my-file-share](../labs/lab-06-media/connect-public-vm-to-my-file-share-1.png)
![Connect myVmPublic to my-file-share](../labs/lab-06-media/connect-public-vm-to-my-file-share-2.png)
![Connect to myVmPublic to Bing](../labs/lab-06-media/connect-public-vm-3-internet-ping.png)

---

## Clean up resources

> 🗑️ To avoid costs, delete the resource group **AZ500LAB06** once the validation is complete.

![Clean Up Resources](../labs/lab-06-media/cleanup-resource.png)


# Lessons Learned

* 🔐 **Service Endpoints** allow secure access to Azure Storage through the **Azure backbone network**, reducing exposure to the public internet.
* 🌐 **Subnet segmentation** (Public vs Private) helps isolate resources and control access to sensitive services.
* 🛡️ **Network Security Groups (NSGs)** enforce traffic rules, such as restricting internet access and allowing only required connections.
* 📦 **Storage account firewall rules** ensure only approved networks or subnets can access storage resources.
* 🧪 **Connectivity testing** from different VMs confirmed that the **Private subnet could access storage** while the **Public subnet was blocked**.

## 🎯 Key takeaway:
Using **service endpoints 🌐, NSGs 🛡️, subnet design 🏗️, and storage firewalls 🔐** creates a **defense-in-depth security architecture** for Azure storage.

