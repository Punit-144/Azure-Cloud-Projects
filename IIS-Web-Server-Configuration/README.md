# IIS-Web-Server Configuration

This repository contains detailed steps for configuring an IIS web server, allocating a static IP to a virtual machine, attaching a data disk, and enabling Hyper-V in Azure. These tasks were completed as part of the Azure Cloud Projects.



### Task 1: Install an IIS Web Server

**IIS (Internet Information Services)**: IIS is a web server software developed by Microsoft. It enables hosting and serving websites, web applications, and other content on the internet or intranet.

#### Steps to Install IIS:

1. **Create a Virtual Machine (VM):**
   - Name: VM1
   - Image: Windows Server 2016 Datacenter
   - Size: Standard_D2s_v3

2. **Add Roles and Features:**
   - Access the VM via RDP.
   - Open the Server Manager Dashboard.
   - Click "Add Roles and Features" and follow the on-screen steps to install the IIS Web Server.

3. **Open IIS Manager:**
   - Launch the default website using IIS Manager.
   - Follow the provided steps and screenshots.

4. **Resolve Access Issue:**
   - Add inbound port rules to ensure the default IIS website is accessible via the public IP address of the VM.

The IIS Web Server is now successfully installed and accessible.

---

### Task 2: Allocate Static IP to VM

**Static IP**: A static IP address is a fixed, unchanging numerical label assigned to a device, as opposed to a dynamic IP that changes periodically.

#### Steps to Allocate Static IP:

1. **Access IP Configuration:**
   - Navigate to the VM's networking section.
   - Select the network interface and open its IP configurations.
   - Observe the default allocation (dynamic).

2. **Check IPV4 Address:**
   - Use PowerShell within the VM to verify its current IPV4 address.

3. **Set Static IP:**
   - Change the IP allocation to static following the detailed steps.

After completing these steps, the IPV4 address will be static (e.g., `10.0.0.20`).

---

### Task 3: Attach a Data Disk to VM

#### Steps to Attach a Data Disk:

1. **Add Disk to VM:**
   - Navigate to VM1 > Disks > Create & Attach a Disk.
   - Set the following details:
     - Disk Name: `DATA disk`
     - Storage Type: `Premium SSD`
     - Size: `4 GB`
     - Host: `Read-Only`

2. **Format and Allocate Disk:**
   - Access the VM via RDP.
   - Open "Create and Format Hard Disk Partitions."
   - Right-click on the unallocated Disk 2, select "New Simple Volume," and follow the wizard to finish allocation.

Disk 2 is now allocated as `Volume F:`.

---

### Task 4: Enable Hyper-V in Azure

**Hyper-V**: Hyper-V is a Microsoft hypervisor that allows running multiple virtual machines on a single physical host. In Azure, Hyper-V provides a fully isolated and customizable environment for VMs.

#### Steps to Enable Hyper-V:

1. **Create a Virtual Machine:**
   - Deploy a new VM in Azure.

2. **Install Hyper-V:**
   - Access the VM via RDP.
   - Open the Server Manager Dashboard.
   - Select "Hyper-V" under Server Roles and install it.

3. **Restart the VM:**
   - After the restart, Hyper-V is enabled.

---

## Screenshots

This repository contains screenshots for every step to assist in understanding and replicating the configuration process. The screenshots are compiled into a PDF for easy access and reference.


---

## Notes

- Ensure proper permissions and resource availability in your Azure subscription before starting.

- Follow the detailed steps in the repository's documentation for each task.



## Author

This project is part of my journey in Azure Cloud Projects. Contributions and feedback are welcome!
