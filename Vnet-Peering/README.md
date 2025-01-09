# Virtual Network Peering Project

This project demonstrates the implementation of **Azure Virtual Network (VNet) Peering**, enabling seamless communication between two virtual networks (VNets) in Azure. Additionally, it covers creating virtual machines (VMs) and establishing connectivity between them.

---

## 📝 Steps to Implement

### **1. Sign in to the Azure Portal**
- Navigate to [Azure Portal](https://portal.azure.com).
- Log in with your Azure account credentials.

### **2. Create Virtual Networks**
- Go to **Create a resource** → Search for **Virtual Network** → Click **Create**.
- Configure the following:
  - Unique name for the virtual network.
  - IP address space.
  - Subnet configuration.
- Click **Create** to complete the setup for the first virtual network (e.g., `VNET1`).

> 🔄 **Repeat**: Follow the same steps to create a second virtual network (e.g., `VNET2`) with a unique name and IP address space.

---

### **3. Peer Virtual Networks**
1. Navigate to the **Virtual Networks** section in the Azure portal.
2. Select the first virtual network (`VNET1`) → Click on the **Peerings** tab → Click **Add**.
3. In the **Peering configuration**:
   - Select the second virtual network (`VNET2`) as the remote virtual network.
   - Configure settings (e.g., allow/deny access between VNets).
   - Provide a unique name for the peering.
4. Click **OK** to establish the peering.

---

### **4. Create Virtual Machines**
- Go to **Create a resource** → Search for **Virtual Machine** → Click **Create**.
- Configure the following for both VMs:
  - Name: `VM1` and `VM2`.
  - Image: **Windows 10 Pro**.
  - Authentication: Provide a username and password.
  - Monitoring: Disable diagnostics.
  - Networking: Assign `VM1` to `VNET1` and `VM2` to `VNET2`.
- Click **Create** to deploy each virtual machine.

---

### **5. Configure Virtual Machines**
1. Use **RDP** to connect to each VM using their **Public IP Address**.
2. In each VM:
   - Turn off **Windows Defender Firewall** for both public and private networks:
     - Search for **Windows Defender Firewall** → Click **Turn Windows Defender Firewall on or off** → Select **Off**.
   - Run **PowerShell** commands:
     - `hostname` (to verify the VM name).
     - `ipconfig` (to view network configuration).

---

### **6. Test Connectivity Between VMs**
- Use PowerShell in `VM1` to ping `VM2`'s IPv4 address:
  ```bash
  ping <IPv4 Address of VM2>

### **7 Use PowerShell in VM2 to ping VM1's IPv4 address:**
ping <IPv4 Address of VM1>

📂 Files Included
    • PDF Documentation:
        • Virtual Network Peering
        • Virtual Machine Connections



💡 Key Learnings
    • Setting up and configuring Azure VNets and Subnets.
    • Implementing VNet Peering for seamless inter-network communication.
    • Managing virtual machines and configuring connectivity using PowerShell.
    • Understanding security configurations with firewalls


🔗 References
    • Official Azure Documentation: https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview