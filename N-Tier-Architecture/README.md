# N-Tier Architecture Implementation on Azure

## Overview

The task involves implementing an N-Tier architecture on the Azure portal. This guide will walk you through the steps to set up the infrastructure and configure it according to the technical requirements.

## Instructions

### 1. Create Virtual Network

- Create a virtual network named `Vnet` in a new resource group called `N-TierRG`.
- Create three subnets within the virtual network:
  - `WebVN`
  - `AppVN`
  - `DatabaseVN`

### 2. Create Virtual Machines (VMs)

- Create three VMs in the `N-TierRG` resource group with the following attributes:
  - **Image**: Windows Server 2016 Datacenter
  - **Size**: Standard_DS1_v2
  - **VM Names**:
    - `WebVM` connected to `WebVN`
    - `AppVM` connected to `AppVN`
    - `DatabaseVM` connected to `DatabaseVN`

### 3. RDP Access to VMs

- Open all the VMs simultaneously using Remote Desktop Protocol (RDP).

### 4. Enable ICMP Protocol

- To enable connectivity between the VMs, enable the ICMP protocol in all three VMs.
  - Go to **Windows Firewall with Advanced Security**.
  - Navigate to **Inbound Rules**.
  - Search for `ICMP (IPv4)` and enable the rule.

### 5. Configure Outbound Rules for DatabaseVM

- **DB Tier should not access any other tier**:
  - Go to **Outbound Port Rules** on `DatabaseVM`.
  - Add an outbound rule that denies access to `AppVM` and `WebVM` subnets by specifying their IP address ranges and setting the action to **Deny**.

### 6. Restrict Internet Access for DatabaseVM

- **Only Web Tier should connect to the internet**:
  - On `DatabaseVM`, add outbound rules to block HTTP and HTTPS traffic:
    - **Destination**: `Internet` (Service Tag)
    - **Action**: **Deny**
    - Select **Service**: HTTPS and HTTP, then click **Add**.

### 7. Configure Outbound Rules for AppVM

- Repeat the same steps as for `DatabaseVM` to restrict internet access on `AppVM`.

### 8. Configure Web Tier Access

- **Web Tier should only access App Tier**:
  - On `WebVM`, go to **Outbound Port Rules**.
  - Add an outbound rule that denies access to the `DatabaseVM` subnet.

### 9. Testing the Configuration

- **Test the technical requirements**:
  - On `DatabaseVM`, open PowerShell and ping the IP addresses of the other VMs (e.g., `10.0.1.0` and `10.0.0.0`). You should receive a "request timeout" response.
  - Test internet access on `DatabaseVM` using Internet Explorer.
  - Perform the same tests on `AppVM` and `WebVM`.

### 10. Final Verification

- Ensure that internet access works as expected and that the security rules are properly applied.

## screenshots

I have created a detailed PDF documentation with screenshots and step-by-step instructions for implementing N-Tier-Architecture. Please refer to the PDF for visual guidance and further details.

## Conclusion

The N-Tier architecture has been successfully implemented on Azure, meeting all technical requirements. Each VM is properly configured with the correct outbound rules, ensuring proper segregation of network access between the tiers.

## References

- Azure Documentation: [Link to official Azure documentation](https://docs.microsoft.com/en-us/azure/)
