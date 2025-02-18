# Deploying Static Website using Load Balancer by ARM Template

## Project Overview

This project demonstrates how to deploy a **static pet shop website** using Azure’s cloud infrastructure. By leveraging **Azure Load Balancer** and **ARM templates**, the deployment ensures:

- **High availability** of the website.
- **Traffic distribution** for scalability and resilience.
- **Automated infrastructure deployment** using Infrastructure as Code (IaC).

## Problem Statement

Static websites often need a scalable and resilient deployment strategy to handle traffic efficiently. Hosting a **pet shop website** on Azure with a load-balanced setup ensures that users experience seamless access without downtime, even if one virtual machine (VM) fails.

## Project Goals

- Deploy the **pet shop static website** on Azure using ARM templates.
- Set up a **Virtual Network (VNet)** with **Subnets** and a **Network Security Group (NSG)**.
- Use an **Azure Load Balancer** to distribute traffic between multiple VMs.
- Host the website on **Azure Virtual Machines (VMs)** and make it accessible via the load balancer’s frontend IP.

## Technologies and Azure Services Used

1. **Azure CLI** - Used for creating and managing resources.
2. **ARM Templates** - Automating resource creation and deployment.
3. **Azure Virtual Machines (VMs)** - Hosting the website.
4. **Azure Load Balancer** - Distributing incoming traffic between VMs.
5. **Nginx** - Used as a web server on the VMs.
6. **Git** - Version control and cloning the website onto the VMs.
7. **Custom Script Extension** - Automating VM configuration during deployment.

## Project Steps

### 1. Website Development
- A **static pet shop website** was created using HTML, CSS, and JavaScript.

### 2. Uploading the Website to GitHub
- The frontend of the website was uploaded to a public GitHub repository: [Pet Shop Website](https://github.com/TaraiPriyanka/arm_template.git).

### 3. Deploying Resources on Azure Using ARM Templates
- **Resource Group:** Created using Azure CLI to contain all resources.
- **Virtual Network (VNet):** Defined in an ARM template with subnets for VM distribution.
- **Network Security Group (NSG):** Configured to allow traffic on ports **22 (SSH) and 80 (HTTP)**.

### 4. Virtual Machines Setup
- **VM 1:** Deployed with networking configurations and an automated script to fetch website files.

  **Custom Script:**
  ```bash
  #!/bin/bash
  sudo apt update
  sudo apt install nginx git -y
  cd /tmp && git clone https://github.com/TaraiPriyanka/arm_template.git mysitee
  sudo rm -rf /var/www/html/index.nginx-debian.html
  sudo cp -r /tmp/mysitee/* /var/www/html/
  ```

- **VM 2:** Deployed with identical configuration to VM 1.

### 5. Load Balancer Configuration
- **Load Balancer:** Configured to distribute traffic between VM 1 and VM 2.
  - **Frontend IP Configuration:** Assigned a public IP for external access.
  - **Backend Pool:** Added both VMs to the backend pool.
  - **Load Balancing Rule:** Defined to balance HTTP traffic (port 80).
  - **Health Probe:** Set up to monitor VM health and ensure continuous availability.

### 6. Testing and Accessing the Website
- The website was accessed through the **Load Balancer’s frontend IP**, ensuring load-balanced traffic distribution.

## How to Use the Pet Shop Website

1. Browse the collection of pet products and services.
2. Read detailed product descriptions.
3. Add favorite items to the cart for purchase.

## Azure Services and Tools Used

- **Azure CLI** - For resource provisioning.
- **Azure Resource Manager (ARM) Templates** - Infrastructure automation.
- **Virtual Network (VNet)** - Secure networking.
- **Network Security Group (NSG)** - Access control.
- **Azure Virtual Machines (VMs)** - Hosting static content.
- **Azure Load Balancer** - Ensuring high availability.
- **Nginx** - Web server for serving static files.
- **Git** - Cloning website files.
- **Custom Script Extension** - Automating VM setup.

## Live Website and Resources

- **Website Link:** [Pet Shop Website](https://github.com/TaraiPriyanka/arm_template.git)
- **Screenshots:**
  - **Resource Group Creation Output**
  - **VNet Deployment Output**
  - **VM 1 Deployment**
  - **VM 2 Deployment**
  - **Load Balancer Setup**
  - **Website Home Page**

## Conclusion

This project successfully demonstrates the deployment of a **highly available static pet shop website** using Azure’s infrastructure. By utilizing an **Azure Load Balancer** and **ARM templates**, we achieved **scalability, high availability, and automated deployments**. The project highlights the potential of **Infrastructure as Code (IaC)** in cloud computing.

## Authors

**Tarai Priyanka, Ganj Bhavana, Yarlagadda Jasmitha, Subhanpuram Thanvi Sree**  
We are passionate about technology and cloud computing. This project demonstrates how **Azure services** can be leveraged for **scalable and resilient** deployments! 🚀

