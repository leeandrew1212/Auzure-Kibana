#  Project Auzure
ELK Stack Deployment, Cloud Security & Virtual Machines information and deployment.
##  ELK Stack Deployment Diagram    
![Elk-Diagram drawio](https://user-images.githubusercontent.com/102629156/161366959-0b0cdc4c-80ca-489c-baa5-fe27d3181251.png)
##  Cloud Security & Virtual Machines Base Diagram
![Cloud Security drawio](https://user-images.githubusercontent.com/102629156/161367105-da6f89e1-e92e-41ee-9bed-496b6728a247.png)

Elk Stack Deployment Diagram, displays a tested and used live ELK environment on Azure. The Cloud Security & Virtual Machines Base Diagram, displays a more detailed example of a base deployment environment without the configuration of Elk Stack seen in the above digram.  
 Select portions of the ELK Stack Diagram, such as the ELK virtual machine may be used to install only certain pieces of it, for example, "Filebeat" launched within the etc/ansible file. The playbook can be found in the CyberSec(Ansible) guidlines below.
##  Ansible Configuration Files 
[CyberSec guidlines for this project](Ansible)
### Filebeat Ansible File
  - Contains the Description of the Topology
  - Access Policies
  - ELK Configuration
     - Beats in Use
     - Machines Being Monitored
  - How to use the Ansible Build
## Topology Description

The overall purpose of this network is to expose a load-balanced and monitored instance of DVWA; an application where penertration testers and security professionals can test their skills and tools.
