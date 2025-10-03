# T-Pot 24.04 - Home Lab Honeypot Setup

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




  
