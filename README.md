# Microsoft Azure – JumpServer Architecture

## Overview
This project demonstrates the implementation of a **secure and cost-effective JumpServer architecture** in **Microsoft Azure**.  
The lab showcases how a single virtual machine with a **public IP address (JumpServer)** can be used to securely access multiple internal virtual machines (**VM1 and VM2**) that do **not** have public IP addresses.

This design reduces exposure to the internet, improves security, and minimises the cost associated with assigning public IPs to every virtual machine.

---

## Technologies Used
- Microsoft Azure
- Azure Virtual Machines (Windows)
- Azure Virtual Network (VNet)
- Network Security Groups (NSGs)
- Public and Private IP addressing
- Azure Portal

---

## Architecture Overview
The architecture consists of:
- **JumpServer VM**
  - Assigned a **Public IP**
  - Acts as a secure entry point
- **VM1 and VM2**
  - No public IP addresses
  - Accessible only via private IPs
- All virtual machines are deployed within the **same Azure Virtual Network**

**Traffic Flow:**

Internet  
⬇  
JumpServer (Public IP)  
⬇  
VM1 / VM2 (Private IP only)

---

## Implementation Steps

### Step 1: Virtual Network and Resource Group
A resource group and virtual network were created to host all virtual machines within a controlled network environment.

---

### Step 2: JumpServer VM Deployment
A virtual machine was deployed as a **JumpServer** with:
- A public IP address
- NSG rules allowing limited inbound access (e.g. RDP)
- Secure administrative access configuration

This server acts as the only externally accessible system.

---

### Step 3: Internal VM Deployment (VM1 & VM2)
Two additional virtual machines (VM1 and VM2) were created with:
- **No public IP addresses**
- Private IP addressing only
- Restricted NSG rules to allow access **only from the JumpServer**

---

### Step 4: Private Connectivity Configuration
Private IP connectivity was configured so that:
- The JumpServer could access VM1 and VM2 internally
- Communication occurred entirely within the Azure Virtual Network
- No direct internet exposure existed for VM1 and VM2

---

### Step 5: Validation and Testing
The setup was validated by:
- Successfully connecting to the JumpServer via public IP
- Accessing VM1 and VM2 from the JumpServer using private IP addresses
- Confirming that VM1 and VM2 were not reachable from the internet

---

## Results
- Secure access to internal VMs achieved
- Public IP exposure reduced to a single entry point
- Azure resource costs minimised
- Improved security posture following best-practice architecture

---

## Screenshots

### Azure JumpServer Virtual Machine
![Azure JumpServer VM](screenshots/microsoft-azure-jumpserver.png)

---

## Key Learnings
- Understanding secure jump-host architecture
- Azure networking fundamentals
- Practical use of private IP addressing
- Cost-optimised cloud design
- Applying security best practices in Azure

---

## Future Enhancements
- Replace public IP access with Azure Bastion
- Implement Just-In-Time (JIT) VM access
- Enable Azure Monitor and Defender for Cloud
- Apply role-based access control (RBAC)
