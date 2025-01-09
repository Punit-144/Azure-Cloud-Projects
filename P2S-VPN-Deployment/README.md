# Point-to-Site (P2S) Configuration in Azure

This folder contains the implementation steps for setting up a secure Point-to-Site (P2S) VPN connection to an Azure Virtual Network (VNet). The configuration enables remote access to resources hosted within the VNet, ensuring secure connectivity over the internet.

## Overview

A Point-to-Site (P2S) connection allows individual client devices to connect securely to an Azure Virtual Network (VNet). This VPN connection is established using Azure AD authentication, enabling remote users to securely access cloud resources over the internet.

## Contents

1. [P2S Architecture](#p2s-architecture)
2. [Steps for Point-to-Site Configuration](#steps-for-point-to-site-configuration)
    - [Step 1: Create a Virtual Network](#step-1-create-a-virtual-network)
    - [Step 2: Create a Virtual Network Gateway](#step-2-create-a-virtual-network-gateway)
    - [Step 3: Create a Virtual Machine](#step-3-create-a-virtual-machine)
    - [Step 4: Create Root and Client Certificates](#step-4-create-root-and-client-certificates)
    - [Step 5: Export the Certificates](#step-5-export-the-certificates)
    - [Step 6: Point-to-Site Configuration](#step-6-point-to-site-configuration)
    - [Step 7: Download the VPN Client](#step-7-download-the-vpn-client)
    - [Step 8: Connect to VPN](#step-8-connect-to-vpn)
    - [Step 9: Enable ICMP Port in the Virtual Machine](#step-9-enable-icmp-port-in-the-virtual-machine)
    - [Step 10: Point-to-Site Connection Established](#step-10-point-to-site-connection-established)
3. [Screenshots](#screenshots)
4. [Conclusion](#conclusion)
5. [References](#references)

## P2S Architecture

The architecture of a Point-to-Site connection in Azure involves a VPN gateway that facilitates the secure connection between client devices and the Azure Virtual Network. The VPN client uses certificates for authentication, ensuring only authorized devices can connect.

## Steps for Point-to-Site Configuration

### Step 1: Create a Virtual Network

- Create a virtual network named `P2SVNet` in the resource group `P2SRG` in the **Central India** region.
- Set the address space to `10.0.0.0/16` and subnet to `10.0.0.0/24`.
- Add a **Gateway Subnet** in the subnet section.

### Step 2: Create a Virtual Network Gateway

- Create a Virtual Network Gateway (`P2SVNG`) with the following settings:
  - **Region**: Central India
  - **Gateway Type**: VPN
  - **VPN Type**: Route-based
  - **SKU**: VpnGw1
  - **Generation**: 1
  - **Virtual Network**: P2SVNet
  - **Public IP**: VNG-PIP
- This deployment typically takes **35-40 minutes**.

### Step 3: Create a Virtual Machine

- Create a Virtual Machine (`VM`) in the same resource group as the virtual network (`P2SRG`).
- Select the **Windows 10 Pro** image.
- In the **Networking** section, connect the VM to the `P2SVNet` virtual network with default subnetting.

### Step 4: Create Root and Client Certificates

- Search for Microsoft Azure root and client certificates and follow the instructions to generate the certificates using PowerShell.
- Use `certmgr.msc` in PowerShell to view the generated certificates.

### Step 5: Export the Certificates

- Export both the root and client certificates.
- For the root certificate, do not export the private key.
- For the client certificate, export the private key and secure it with a password.

### Step 6: Point-to-Site Configuration

- Go to **Virtual Network Gateway** (VNG), select **Point-to-Site Configuration**, and click **Configure Now**.
- Set the following:
  - **Address Pool**: `192.168.0.0/24`
  - **Tunnel Type**: SSTP (SSL)
  - **Authentication Type**: Azure Certificate
  - Paste the content of the **Root Certificate** into the **Public certificate data** section.

### Step 7: Download the VPN Client

- After configuring, click **Download VPN Client**.
- This will download a folder named `P2SVNG`. Extract it and install the VPN client that corresponds to your local machine.

### Step 8: Connect to VPN

- Go to your local machine's **VPN settings**, and you should see `P2SVNet` listed.
- Click **Connect** to establish the VPN connection.

### Step 9: Enable ICMP Port in the Virtual Machine

- Connect to the VM using **RDP**.
- In the VM, go to **Advanced Firewall Options** and enable the **ICMP rule** in the **Inbound Rules** to ensure smooth Point-to-Site connection.

### Step 10: Point-to-Site Connection Established

- Once the ICMP rule is enabled, the Point-to-Site connection will be successfully established, and you can securely access the Azure VNet resources.

## Screenshots

I have created a detailed PDF documentation with screenshots and step-by-step instructions for configuring Point-to-Site connectivity. Please refer to the PDF for visual guidance and further details.

## Conclusion

This configuration ensures that individual client devices can securely connect to the Azure Virtual Network using Point-to-Site VPN, leveraging Azure AD authentication for enhanced security and access control.

## References

1. [Microsoft Azure Documentation on Point-to-Site VPN](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about)
2. [YouTube - Learning about Azure VPN Setup](https://www.youtube.com)
3. [PowerShell Commands for Certificate Generation](https://learn.microsoft.com/en-us/powershell/azure/)


