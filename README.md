# T-Pot 24.04.0 - Home Lab Honeypot Setup AWS EC2

## Description

This project consists of the initial setup, execution, and monitoring procedures that took place for setting up a honeypot home lab, with the use of T-Pot 24.04.0 which was hosted on Amazon's AWS EC2 Virtual Machines. T-Pot 24.04.0 comes with its own NGINX dashboard, where you can access different utilities that can trace movement on the system and evaluate the security vulnerabilities that are present within the system. This experiment was completed for educational purposes and to learn more about System Hardening and how to prevent breaches from occurring in the future.

T-Pot can be found here: https://github.com/telekom-security/tpotce/

## What is a Honeypot?

Honeypots are systems or servers that are set up as a form of diversion to attract potential attackers and divert these attackers from the real systems or servers. Usually, if honeypots are created at an advanced level, they can protect against potential data theft, as attackers will be unsure of which system is, in fact, a real system.

## Configuring T-Pot 24.04.0

The following system requirements are needed for T-Pot 24.04.0 to function properly:
* Debian 11
* 8-16GB of RAM
* Free Storage Space must be >=128GB

Without these requirements, issues can arise upon deployment of T-Pot and produce incorrect results in the monitoring procedures.

### Login Details I Used

| Username | Password | 
| -------- | -------- |
| cybers3c-UWL | CL9x(&^mQ1@ |

The reasoning behind using a more complex password was to enhance protection as much as possible to find out what type of methods the attackers used. These details were used to log in to the T-Pot Web UI and access all the necessary tools for investigating the overall activity taking place across the honeypots.

## Setting Up The Victim Machine

<img width="1452" height="549" alt="Setting-Up-Victim" src="https://github.com/user-attachments/assets/7bab5289-5a08-483d-bffa-78d2836db508" />

Victim Machine was set up on AWS EC2 virtual servers; therefore, a personal network is not used, as this could expose your network and draw unwanted attention from attackers. Here, all the ports were managed effectively to assign to each designated use case. All ports used were in TCP protocol format. Creating a security group within AWS enabled me to restrict access to specific ports, while still allowing the owner to access them through successful authentication.

### Ports in Security Group

| Port(s) | Source(s) | Usage/Purpose |
| ------- | --------- | ------------- | 
| 1-64000 | 0.0.0.0/0 & ::0/ | Open to the general public, allowing all forms of attackers to try and crack into the system through these ports |
| 64295   | <VM_IP>/32 | Access for SSH to use T-Pot Management Resources, Windows PowerShell is used to establish a secure SSH connection |
| 64297   | <VM_IP>/32 | Access to NGINX T-Pot Dashboard, where all the tools are used such as Kibana, Suricata, Elastic, Spiderfoot, etc. (all activity monitoring software) |
| 64294   | <VM_IP>/32 | Access to T-Pot cockpit showing real-time activity and geographical map with ping updates |

###  Create New Instance EC2

<img width="600" height="600" alt="Settings_New_Instance" src="https://github.com/user-attachments/assets/b30f2258-1720-4f5c-8b63-6b3431e4f607" />

A new Amazon Machine Image (AMI) is created by selecting all the necessary features your VM requires. In this case, for T-Pot deployment, we used Debian 11 and selected t3.large as the virtual server type for enhanced processing speeds and smoothness throughout the full course of its running time. 

t3.large consists of the following specifications:
* 2 vCPUs
* 8GiB RAM

### Full Setup Parameters

| Virtual Server Type | Storage Size | Operating System |
| ------------------- | ------------ | ---------------- |
| t3.large            | 128 GiB      | Debian 11        |

Firewall Security Group would be the one that we set up earlier using the different ports, and ensuring that some ports are left open purposely and others closed off for restricted access or denial. In this case, it was named 'TPot-Security', which I selected to deploy with this configuration.

### Key Pair Creation

<img width="386" height="402" alt="Key_Pair_Creation" src="https://github.com/user-attachments/assets/1fee5756-f627-42b6-9847-b36b66092a98" />

Key Pair creation is necessary for a secure and successful SSH connection between clients. Within the EC2 setup process, we create a PEM key pair file, which will appear as a '.pem' file on our machine, this key pair is then used to authenticate our connection via OpenSSH for later on in the project. The encryption mode that is used for PEM files is stated as RSA, which is the Rivest-Shamir-Adleman cryptography method (public + private keys relied upon).

### Enabling Elastic IP Addresses

<img width="400" height="400" alt="Elastic_IP_Addrs" src="https://github.com/user-attachments/assets/66bfce4d-94a0-44be-81db-87e47857ddf6" />

We enable Elastic IP Addresses in order to make our IP address static for the whole duration of the instance, so if the instance is rebooted or turned off, we still retain the exact same IP address. The elastic IP address is allocated to your AWS account; each account has a different elastic IP address. The usage of elastic IP addresses allows for a seamless connection and removes the extra steps to alter information to match the 'changed IP address' each time the instance is rebooted.

After all of these steps have been completed, we are ready to proceed with setting up the other parts of the honeypot project.

## Establishing SSH Connection with AWS Virtual Server

Luckily enough, AWS EC2 provides a simple guide on how to establish a SSH connection securely which is shown in the screenshot below, we follow this guide to use our PowerShell in gaining this SSH connection.

<img width="400" height="400" alt="Connect-SSH-Show" src="https://github.com/user-attachments/assets/6a81a53f-d160-4586-b094-7d311ccdba13" />







  
