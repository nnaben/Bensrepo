# Bensrepo

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.	

!(https://github.com/nnaben/Bensrepo/blob/main/Diagrams/Elk-diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __yml___ file may be used to install only certain pieces of it, such as Filebeat.

  - PLAYBOOK FILE:
  - **Bensrepo/Ansible/Elk-install.yml**
  -  ![https://github.com/nnaben/Bensrepo/blob/main/Ansible/install-elk.yml]

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to ehnacing security by restricting unauthorized traffic to the network.

- What aspect of security do load balancers protect?
	- **Load balancers are good in defending or protecting the corporate server from Distributed Denial of Service (DDOS) attacks.
**
-  What is the advantage of a jump box?
	- **Jump box is a hardened and monitored device/machine that is used to access and manages other devices in different security zones. it provides a secure standpoint when connecting to untrusted networks**

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system use
 - What does Filebeat watch for?
	**- It watches for log data, centralizes and forwards it to Logstash for enrichment**
	
	![https://github.com/nnaben/Bensrepo/blob/main/Diagrams/Filebeat-kibeana.PNG]

 _What does Metricbeat record?
	- **It periodically collects metrics from operating systems and other sevices running in a server**
 	![https://github.com/nnaben/Bensrepo/blob/main/Diagrams/Metribeat-kibeana.PNG]


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name        | Function        | IP Address  | Operating System|
|-------------|-----------------|-------------|-----------------|
| Jump Box    | gateway         |10.0.0.4     | Linux           |
| web-1       | webserver       |10.0.0.5     | Linux           |
| web-2       | webserver       |10.0.0.7     | Linux           |
| web-3       | webserver       |10.0.0.7     | Linux           |
| Elk         | webserver       |10.1.0.4     | Linux           |
|Load balancer| security/traffic|52.170.64.162| Linux           |
|	      |    distribution |             |	                |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ___ELk__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 10.0.0.4 73.43.21.5  

- _Whitelisted IP addresses: 73.43.21.5 which is my home public address. Whitelisted means that it is allowed access to for the whole network. it is not blocked
    
	
Machines within the network can only be accessed by The jump box/ancible.

- _Which machine did you allow to access your ELK VM? What was its IP address?_**The jumpbox with IP 10.0.0.4**

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | 10.0.0.5, 10.0.0.6, 10.0.0.7|
|  web-1   | no                  | 10.0.0.4, 10.0.0.6, 10.0.0.7|
|  web-2   | no                  | 10.0.0.4, 10.0.0.6, 10.0.0.7|
|  web-3   | no                  | 10.0.0.4, 10.0.0.5, 10.0.0.6|
|  Elk     | no                  | 10.0.0.4, 73.43.21.5|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because .
- _What is the main advantage of automating configuration with Ansible?
	_**It minimizes the risk of errors in the configuration files and it saves time**

The playbook implements the following tasks:
- _Explanation of the steps of the ELK installation play. E.g., install Docker; download image; etc._
	- **It first installs docker.io and downloads image
	- it downloads and install python pip3 module
	- it maps out the required memory size
	- it downloads and installs elk container and enables service docker on boot**.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![https://github.com/nnaben/Bensrepo/blob/main/Diagrams/docker-ps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _List of IP addresses of the monitored machines_
	-10.0.0.5
	-10.0.0.6
	-10.0.0.7

We have installed the following Beats on these machines:
- _Beats successfully installed_

 -** filebeat-7.4.0-amd64.deb
 - metricbeat7.4.0-amd64.deb**

These Beats allow us to collect the following information from each machine:
- _Explanation of the kind of data each beat collects_:
 	- Filebeat: collects all log files like application logs, error logs etc.
 	- metricbeat: This collects metric data like CPU and Memory data from the server machines.

### Using the Playbook 

SSH into the control node and follow the steps below:
- Copy the playbook__config___ file to _/etc/ansible/roles____.
- Update the __hosts___ file to includeVirtual Machines IP addresses.
- Run the playbook, and navigate to __/etc/ansible__ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
-  Which file is the playbook? **All yml files (eg Elk-install.yml)**
-  
-  ![https://github.com/nnaben/Bensrepo/blob/main/Ansible/install-elk.yml]

-  Where do you copy it?_**/etc/ansible/files**
-  Which file do you update to make Ansible run the playbook on a specific machine? The hosts file - ?_/etc/ansible/hosts

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
	- **Inside filebeat-config or metricbeat config, you add the ip addresses and port numbers of the machines to the hosts**
- _Which URL do you navigate to in order to check that the ELK server is running?
	-** http://<Public Ip>:5601/kibana**


