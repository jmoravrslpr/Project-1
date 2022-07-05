# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


![azure Diagram](https://user-images.githubusercontent.com/97639303/177405772-d17cc354-5f98-43e9-a88e-8f71d202b874.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

 ansible.yml
ansibleinstall-elk.yml.TXT
metricbeat-playbook.TXT
filebeat-playbook.yml.TXT

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.

The Load balancers ensure the following purposes:
1. The RedTeam load balancer will distribute web-1 and web-2 client request and network load across all servers on the network. 
2. It will allow more ease in expanding the network and ease the loads of a dedicated server. CIA triad is enhanced.
3. Will aid in submitting request to onther servers across the LAN, WAN and the internet.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
Filebeat collects data about the file system, and this is sent to Elasticsearch on the ELK server.

Metricbeat Collects data to help with the assesment an operational state of the workstations on the network and send those metrics to Elasticsearch on the ELK server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| JumpBox | Gateway   | 10.0.0.1 | Linux UBUNTU 18.4 |
|---------|-----------|----------|-------------------|
| WEB1    | DVWA      | 10.0.0.5 | Linux UBUNTU 18.4 |
| WEB2    | DVWA      | 10.0.0.7 | Linux UBUNTU 18.4 |
| ELKVM   | ELK Stack | 10.2.0.4 | Linux UBUNTU 18.4 |
|         |           |          |                   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMP-BOX-PROVISIONER machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
User workstation local IP address through the SSH PORT22.

Machines within the network can only be accessed by JUMP-BOX MACHINE.
JUMP-BOX IP:10.0.0.1

A summary of the access policies in place can be found in the table below.

|   Name   | Publicly Accessible | Allowed IP Addresses |   |
|:--------:|:-------------------:|:--------------------:|---|
| Jump Box | Yes                 | SSH via Admin's IP   |   |
| WEB1     | No                  | 10.0.0.5             |   |
| WEB2     | No                  | 10.0.0.7             |   |
| ELK      | No                  | 10.2.0.4             |   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it will ensure less chances for mistakes.

ansible.yml

ansibleinstall-elk.yml.TXT

The ansible playbook allows for the implenation and inital setup much more efficient and easliy replicable to addional machines in the furutre. Imaging a machine in much more effcient. 

The playbook implements the following tasks:

Install Docker,facilitates instalation of containers and Python-pip. Install Docker Python Module Increases Virtual Memory and launches a the ELK container with the ports 5601, 9200, 5044.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps](https://user-images.githubusercontent.com/97639303/177424896-2810fe77-60fa-40b9-a486-9ad46beb3a04.jpg)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
WEB-1 10.0.0.5
WEB-2 10.0.0.7

We have installed the following Beats on these machines:

filebeat-playbook.yml.TXT
![module status](https://user-images.githubusercontent.com/97639303/177425478-c42bc32d-ae7e-48c5-bbcc-45a776096e8e.jpg)

metricbeat-playbook.TXT
![mod stat](https://user-images.githubusercontent.com/97639303/177425623-933b19cd-7b9c-4026-8db4-bbcadf16bfaf.jpg)

These Beats allow us to collect the following information from each machine:
File beat collects log files from applications and databases. 
Metricbeat monitors the Network, machines and other stats.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to ansible container.
- Update the configuration file to include the IP of the ELK host server.
- Run the playbook, and navigate to http://(vmip):5601/app/kibana to check that the installation worked as expected.


