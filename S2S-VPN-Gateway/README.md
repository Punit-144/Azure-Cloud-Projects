# Site-to-Site Connection

## Introduction
This documentation aims to provide a comprehensive understanding of Site-to-Site Connection in Microsoft Azure, a solution that enables secure communication between on-premises networks and Azure Virtual Networks (VNets) over the internet.

## What is Site-to-Site Connection?
Site-to-Site (S2S) VPN connects on-premises networks to Azure VNets, enabling businesses to extend their data centers to the cloud. This solution provides access to resources like virtual machines, databases, and applications hosted in Azure.

## Benefits of Site-to-Site Connection:
- **Hybrid Connectivity**: Enables organizations to maintain a hybrid infrastructure using both on-premises and cloud resources.  
- **Security**: Data is transmitted securely over an encrypted VPN tunnel.  
- **Scalability**: Azure's global network ensures reliable and scalable connectivity.  
- **Cost-Effective**: Eliminates the need for dedicated hardware, utilizing the internet for the connection.

---

## Architecture

---

## Steps to Establish Site-to-Site Connection

### Step 1 - Create a Resource Group
Create a Resource Group named **OnPremRG** in the **Central India** region.

---

### Step 2 - Create a Virtual Network
Create a virtual network named **AzureVnet** in the **Central India** region within the **AzureRG** resource group. Use the default subnet.

---

### Step 3 - Create a Virtual Machine
Create a virtual machine named **AzureVM** in **AzureRG** with the **Windows Server 2019 Datacenter** image and the **Standard_D2s_V3** size. Use the default subnet in the networking section.

---

### Step 4 - Create a Virtual Network Gateway
Using the **AzureRG** resource group, create a virtual network gateway named **AzureVNG**.  
- **Gateway Type**: VPN  
- **VPN Type**: Route-Based  
- **SKU**: VpnGw1  
- **Generation**: Generation1  
- **Virtual Network**: AzureVNet  
- **Public IP**: Create a new one, named **VNG-PIP**.  
This deployment will take approximately 35-40 minutes.

---

### Step 5 - Create a VM in On-Premise Resource Group
Create a virtual machine named **OnPremVM** in the **OnPremiseRG** resource group. Use **Windows Server 2019 Datacenter** as the image and **Standard_D2s_V3** as the size.

---

### Step 6 - Install RRAS Server
Log in to the **OnPremVM** using RDP. Install the **Routing and Remote Access Service (RRAS)** following the provided procedure.

---

### Step 7 - Create a Local Network Gateway (LNG)
Create a Local Network Gateway named **AzLNG** using the **OnPremVM**'s IP address and the address space of the **AzureVNet**. Review and create the gateway.

---

### Step 8 - Create a Site-to-Site Connection
Using **AzLNG**, create a Site-to-Site connection named **AzuretoOnPrem**.  
- **Connection Type**: Site-to-Site  
- **Virtual Network Gateway**: **AzureVNG**  
- **Local Network Gateway**: **AzLNG**  
- **Shared Key**: Define and remember it for future use.  
- **IKE Protocol**: IKEv2  
Review and create the connection.

---

### Step 9 - Configure the RRAS Server
Connect to **OnPremVM** using RDP. Open **Server Manager**, go to **Tools**, and launch **Routing and Remote Access**. Right-click **OnPremVM (local)**, select **Configure and Enable Routing and Remote Access**, and follow the steps shown in the screenshots.

---

### Step 10 - Configure the Connection on RRAS Server
Follow the steps in the screenshots to establish the connection between the **On-Premises Network** and **Azure** using the **RRAS** server.

---

### Step 11 - Test Connectivity
Connect to both **AzureVM** and **OnPremVM** using RDP.  
- Before testing connectivity, enable the **ICMP inbound rule** on both VMs through advanced firewall settings.  
- After enabling ICMP, ping both VMs to verify the connection.

---

**Site-to-Site Connection is now established!**

---

This structured process ensures a secure and functional Site-to-Site connection between on-premises and Azure environments, enabling seamless communication for business applications and resources.
