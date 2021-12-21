## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

![CloudNetwork drawio](https://user-images.githubusercontent.com/89550625/146825868-b2752801-4712-4ae8-b983-e0b8878f41a6.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

Ansible Docker Files
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/ansible.cfg
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/hosts
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/playbook.yml

ElkStack Files
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/elkplaybook.yml
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/filebeat-config.yml
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/filebeat-playbook.yml
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/metricbeat-config.yml
https://github.com/bestfriendkyle/ElkStack_Project/blob/main/Ansible/metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

What aspect of security do load balancers protect?
  The load balancers ensure that traffic is evenly distributed between Web-1 and Wed-2 virtual machines. Having two Virtual Machines also ensures that the DVWA is accessable if one of the VMs is down. This also protects availablity in the event of a DDoS attack.
What is the advantage of a jump box?
  The network takes advantage of a jump box provisioner. This allows for both Web-1 and Web-2 to be updated and modified from a single jump box. This preserves the continuity of the network and ensures that any changes and updates made to the DVWA VMs will be the same across the network. 
  
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics from the OS and system files.
Filebeat: A lightweight shipper that forwards log data to your Kibana dashboard. Specifically, it looks for changes in the system files. 

Metricbeat: A lightweight shipper that helps monitor each server by collecting metrics from system an services running on each of the servers. 

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| JumpBox-provisioner | Gateway  | 10.1.0.4   | Linux            |
| Web-1   | Webserver | 10.1.0.7 | Linux |
| Web-2    | Webserver| 10.1.0.8 | Linux |
| ElkServer    | Cloud | 10.0.0.4 | Linux |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the JumpBox-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
97.117.83.***
165.214.37.***
97.117.150.***

Machines within the network can only be accessed by SSH.
Only the JumpBox-Provisioner was allowed to access the Webservers and Elk Stack via SSH. 
The DVWA and Kibana were accessable throught a web browser from the IP addresses listed above. 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses | Port |
|----------|---------------------|----------------------|----------------------|
| JumpBox-Provisionser | No              | 97.117.83.###, 165.214.37.###, 97.117.150.### | 22 |
| Web-1    | No                    |97.117.83.###, 165.214.37.###, 97.117.150.#### | 80 |
| Web-2   | No                    |97.117.83.###, 165.214.37.###, 97.117.150.#### | 80 |
|  Elk Stack        | No                    | 97.117.83.###, 165.214.37.###, 97.117.150.#### | 5601 |    

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually.

Automating the process includes the following advantages.

- Quickly deploy or re-deploy the Elk Stack

- Documentation of deployment is easly seen on the JumpBox-Provisioner.

- Consistantly install the Elk Stack across multiple VMs. 

The playbook implements the following tasks:
- Installs Docker_TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Installs Python Pip
- Installs the Docker Python module
- Increases memory usage on the Elk Stack VM
- Downloads and launches the Docker Elk container
- Enables the Docker service.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Web-1   | Webserver | 10.1.0.7 |
| Web-2    | Webserver| 10.1.0.8 |

We have installed the following Beats on these machines:
| Web-1   | Webserver | 10.1.0.7 |
| Web-2    | Webserver| 10.1.0.8 |

These Beats allow us to collect the following information from each machine:

Filebeat: Changes to system log files such as system.log and error.long

Additional information for Filebeat can be found at https://www.elastic.co/beats/filebeat

Metricbeat: Tracks metrics for CPU usage, memory, file system, disk IO, and network IO statistics.

Additional information for Metricbeat can be found at https://www.elastic.co/beats/metricbeat
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.ym and metricbeat-playbook.yml files to /etc/ansible directory on your JumpBox-Provisioner VM.
- Update the host file to include the network IP address for your Elk Stack VM.
- Run the playbook, and navigate to http://[Public Elkstack IP Address]:5601/app/kibana to check that the installation worked as expected.
_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
