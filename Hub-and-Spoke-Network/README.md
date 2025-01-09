# Hub and Spoke Architecture

Our task here is to establish a connection between hub and spoke.

## Conceptual Overview

A hub and spoke network is a common transportation or communication system design that involves a central hub connecting to multiple spoke locations. It is widely used in various industries, including transportation, logistics, telecommunications, and airline industries. The concept of a hub and spoke network is also applicable to other fields, such as data distribution and organizational structures.

In a transportation context, the hub and spoke network consists of a central hub (usually a major transportation centre, such as an airport, seaport, or distribution centre) that serves as a focal point for routing and coordinating traffic to and from various spoke locations. The spoke locations are typically smaller regional destinations or distribution points that are connected directly to the hub.

### Key characteristics of a hub and spoke network:

1. **Central Hub**: The central hub is the primary point of consolidation and distribution in the network. It handles a significant volume of traffic and serves as a transfer point for passengers, cargo, or data.
2. **Spoke Locations**: Spoke locations are connected to the central hub but not directly to each other. They act as feeder points, gathering and distributing traffic to and from the hub.
3. **Efficient Routing**: The hub and spoke model allows for efficient routing and connectivity between multiple spoke locations and the central hub. It reduces the number of direct connections required, making the system more manageable and cost-effective.
4. **Concentration of Resources**: By centralizing operations at the hub, resources such as personnel, equipment, and infrastructure can be concentrated, leading to potential cost savings and increased operational efficiency.
5. **Flexibility and Scalability**: The hub and spoke network provides a scalable structure that can be adapted to changes in demand and operational requirements. It allows for the addition or removal of spoke locations with minimal disruption to the overall network.
6. **Improved Connectivity**: Spoke locations may have limited direct connections to other spokes, but they gain increased connectivity through the central hub, enabling access to a wider network.

### Examples of hub and spoke networks include:
- **Airline Routes**: Many airlines use hub and spoke networks, with major airports acting as hubs that connect to numerous regional and international destinations.
- **Package Delivery**: Courier and package delivery companies often use hub and spoke networks to efficiently distribute packages from central sorting centers to regional distribution centers and then to local delivery routes.
- **Telecommunications**: Telecommunication companies may employ hub and spoke networks to manage data traffic efficiently, with major data centers serving as hubs connected to smaller regional data centers.

Overall, the hub and spoke network design is a widely adopted approach that offers advantages in terms of efficiency, cost-effectiveness, and scalability in various industries.

## Architecture

Now we will follow the following instructions to complete the task.

### Step 1: Create a Resource Group and Virtual Networks

1. **Create a Resource Group** named `Hub_Spoke_RG`.
2. Inside the resource group, create three virtual networks:
   - **Hub_Vnet**
   - **Spoke_1_Vnet**
   - **Spoke_2_Vnet**

### Step 2: Create VNet Peering

1. In **Hub_Vnet**, navigate to `Peerings` and click on `Add`.
2. In the `Add Peering` window:
   - Name the peering link **Hub_to_Spoke1** for creating VNet Peering between `Hub_Vnet` and `Spoke_1_Vnet`.
   - In the `Remote Virtual network` section, name the peering link **Spoke1_to_Hub** and select `Spoke_1_Vnet`. Click `Add`.
3. Similarly, create another VNet Peering named **Hub_to_Spoke2**. In the `Remote Virtual network` section, name the peering link **Spoke2_to_Hub** and select `Spoke_2_Vnet`. Click `Add`.

### Step 3: Create Virtual Machines

1. Create three virtual machines in the `Hub_Spoke_RG` resource group:
   - **Hub-VM**
   - **Spoke1-VM**
   - **Spoke2-VM**
   - Use **Windows Server 2019 Datacenter** as the image and **Standard_B2s** as the size.

### Step 4: Test Connectivity

1. Login to all three VMs using RDP.
2. Enable the ICMP inbound rule in all three VMs.
3. In each VM, open Command Prompt and run `ipconfig` to know the IP addresses:
   - **HubVM** – IP = 10.0.0.4
   - **Spoke1-VM** – IP = 10.1.0.4
   - **Spoke2-VM** – IP = 10.2.0.4
4. Use the `ping` command in all three VMs to verify connectivity.

### Step 5: Create and Configure the Route Table

1. Search for `Route Table` in the Azure portal.
2. In the `Create Route Table` wizard, select the resource group `Hub_Spoke_RG`, the region **Central India**, and name the route table **Hub_to_Spoke_RT**. Select **No** for Propagate gateway routes and click `Review + Create`. After reviewing, click `Create`.

### Step 6: Configure Routes in the Route Table

1. In the `Hub_to_Spoke_RT`, go to `Routes` on the left side and click on `Add`.
2. In the `Add route` window:
   - Name the route **Spoke1_to_Spoke2**.
   - Set the destination type as **IP Address**.
   - In the destination IP addresses, write the IP address space of `Spoke2_Vnet` (10.2.0.0/16).
   - Set the Next hop type as **Virtual Appliance** and in the hop address, write the private address of the Hub VM (10.0.0.4). Click `Add`.
3. Similarly, create another route named **Spoke2_to_Spoke1** with the destination IP address of `Spoke1_Vnet` (10.1.0.0/16) and the hop address of `Spoke1-VM` (10.1.0.4).

### Step 7: Enable IP Forwarding

1. Connect to **Hub-VM** using RDP.
2. Open PowerShell and run the following command:

Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters -Name IpEnableRouter -Value 1

This command enables IP routing on the Windows system.
3. Restart the Hub-VM.
4. Ping the VMs from each other to verify connectivity.

### Task Completion

The hub and spoke network is now successfully set up and verified with appropriate routing and security configurations.

## Conclusion

In this exercise, we successfully implemented a hub and spoke architecture in Azure by establishing virtual network (VNet) peering, configuring route tables, and enabling IP forwarding to ensure smooth connectivity between the hub and spoke virtual networks. By using VMs in each network, we verified connectivity through ping tests and validated that traffic routing and IP forwarding were functioning as expected. The hub and spoke model allows for scalable and efficient network configurations, with centralized management at the hub, making it an ideal choice for distributed systems.

This configuration can be further customized to meet specific organizational needs, such as adding more spoke networks or modifying routing rules to optimize traffic flow. Overall, the task was completed successfully, showcasing the power of Azure's network infrastructure capabilities.

## References

1. Microsoft Azure Documentation on Virtual Network Peering: [https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)
2. Microsoft Azure Documentation on Route Tables: [https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table)
3. Microsoft Azure Documentation on Virtual Machines: [https://learn.microsoft.com/en-us/azure/virtual-machines/](https://learn.microsoft.com/en-us/azure/virtual-machines/)

## Screenshots

I have created a detailed PDF documentation with screenshots and step-by-step instructions for implementing N-Tier-Architecture. Please refer to the PDF for visual guidance and further details.
