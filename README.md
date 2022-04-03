#  Project Azure
ELK Stack Deployment, Cloud Security & Virtual Machines information and deployment.
##  ELK Stack Deployment Diagram    
![Elk-Diagram drawio](https://user-images.githubusercontent.com/102629156/161366959-0b0cdc4c-80ca-489c-baa5-fe27d3181251.png)
##  Cloud Security & Virtual Machines Base Diagram
![Cloud Security drawio](https://user-images.githubusercontent.com/102629156/161367105-da6f89e1-e92e-41ee-9bed-496b6728a247.png)

Elk Stack Deployment Diagram, displays a tested and used live ELK environment on Azure. The Cloud Security & Virtual Machines Base Diagram, displays a more detailed example of a base deployment environment without the configuration of 
Elk Stack seen in the above diagram.  

Select portions of the ELK Stack Diagram, such as the ELK virtual machine may be used to install only certain pieces of it, for example, "Filebeat" launched within the etc/ansible file. The playbook can be found in the "Ansible Files" below.

##  Ansible Configuration Files 
[Ansible Files](Ansible)
### Filebeat Ansible File
  - Contains the Description of the Topology
  - Access Policies
  - ELK Configuration
     - Beats in Use
     - Machines Being Monitored
  - How to use the Ansible Build
## Topology Description

The overall purpose of this network is to expose a load-balanced and monitored instance of DVWA; an application where penetration testers and security professionals can test their skills and tools.

A Load Balancer ensures traffic is distributed across a number of servers to maintain a balanced flow within the network. In this case it's an Application Load Balancer, which distributes network traffic directly to users. Restricting heavy traffic from slowing or crashing the network, "DDoS Attack". The benefit of a Jump box provides security, backups, and broad customizations acting such as the heart of the system.

Integrating an Elasticsearch, Logstash, & Kibana, (ELK) allows users to monitor the vulnerable virtual machines for changes to the data's logs, and events. System's applications, infrastructures, clickstreams, performance etc. A Filebeat for example gathers, parse, & augment the data. A Metricbeat records metrics along with statistics from the operating system and services running on the server.

 - The configuration details of each machine may be seen in the below table.

| Name               | Function            | IP Address | Operating System |
|--------------------|---------------------|------------|------------------|
| JumpBoxProvisioner | Gateway             | 10.0.0.4   | Linux            |
| Web-1              | AVS Virtual Machine | 10.0.0.5   | Linux            |
| Web-2              | AVS Virtual Machine | 10.0.0.6   | Linux            |
| ELK-Server         | Gateway             | 10.1.0.4   | Linux            |

## Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JumpBoxProvisioner can accept connections from the internet. Access to this machine is only allowed from the following IP addresses, 10.0.0.5 and 10.0.0.6.

Machines within the network can only be accessed by the ELK VM such as Web-1 (10.0.0.5) and Web-2 (10.0.0.6).

 - A brief summary of the access policies in place can be seen in the below table.

| Name               | Publicly Accessible | Allowed IP Addresses  |
|--------------------|---------------------|-----------------------|
| JumpBoxProvisioner | Yes/No              | (10.0.0.5) (10.0.0.6) |
| ELK-Server         | Yes/No              | (10.0.0.5) (10.0.0.6) |

## ELK Configuration

Ansible was used to automate configuration of the ELK virtual machine found in [Ansible Files](Ansible). No configuration was performed manually, as ansible can install an updated version of a specific type of software on all listed IP address within that file at once cutting time and error in half.

### The ELK Ansible File Playbook implements the following tasks:

<img width="451" alt="GTELK yml" src="https://user-images.githubusercontent.com/102629156/161421579-6807a561-6900-492e-bf8d-b69d8ceb3237.png">

### The screenshot below displays the result of running `docker ps` after successfully configuring the Elk instance:

<img width="451" alt="Elk Docker" src="https://user-images.githubusercontent.com/102629156/161421946-88793e17-113e-41b8-a702-cca686b06143.png">

## Target Machines & Beats

This ELK server is configured to monitor Web-1 (10.0.0.5) and Web-2 (10.0.0.6). We have installed the following Beats on these machines; Filebeat, and Metricbeat.

### These Beats allow us to collect the following information from each machine:

#### Filebeat

Filebeat collects a variety of information such as logs, the amount of clicks, and host changes. A brief pictured display can be seen below.

<img width="960" alt="Filebeat Dashboard" src="https://user-images.githubusercontent.com/102629156/161424179-6a716a56-29df-4856-ae8a-d3732402e3a6.png">

#### Metricbeat

Metricbeat provides vivid information on a broad level of things such as user usage, global traffic, high and low load traffic. A detailed image can be seen below.

<img width="960" alt="Metrics Web-1" src="https://user-images.githubusercontent.com/102629156/161424713-b516204f-f024-42b8-9ee9-44935b2d4c27.png">

## Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned.

### SSH into the control node and follow the steps below:
 - Copy the downloaded Filebeat and Metricbeat Config to your `/etc/ansible` directory.
 - Update the Ansible Config to include the remote username for the playbook.
 - Run the playbook and navigate to Kibana module status click check data to see if the installation was successful such as displayed data of your machines.
 
 Create a playbook.yml for Filebeat and Metricbeat, copy it to the `/etc/ansible` directory. Next update the "hosts" file within the ansible directory to install the playbook on the wanted machine's by listing their IP address within [webservers]. To specify which machine to install the Elk server on versus which to install Filebeat on, you must label the config file name above the targeted IP address you want to install the software on. A display can be seen below.

# Ex 2: A collection of hosts belonging to the 'webservers' group

[webservers]
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.6 ansible_python_interpreter=/usr/bin/python3
[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3

Last of all to check finalization of a successful ELK environment you must navigate to Kibana's website with your ELK's Public IP listed here, http://[ELK Public IP]/app/kibana displaying a similar image below.

<img width="960" alt="Kibana" src="https://user-images.githubusercontent.com/102629156/161428451-20031420-59eb-4b00-b7c7-6dedbe6904cb.png">
