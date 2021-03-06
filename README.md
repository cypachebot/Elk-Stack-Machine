# Elk-Stack-Machine
Virtual Machines
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/cypachebot/Elk-Stack-Machine/blob/1a55f6b46fe1cf09e6b2124736e15b4ae095c358/Elk%20Server%20Diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the README file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/cypachebot/Elk-Stack-Machine/blob/main/ansible/my-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- In the configuration we include Filebeat to collect log events, for files and or locations in the VM.
- On the other hand Metricbeat collects metrics and statistics from the operating system and other processes running on the server.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Webserver | 10.0.0.9   | Linux            |
| Web-2    |Webserver | 10.0.0.8   | Linux            |
| Elk-New-Server   |Monitoring| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 40.122.30.120

Machines within the network can only be accessed by the jump box.
-The Jump Box Provisioner can access The Elk Machine by:
-Port: 22
-Port_5601

A summary of the access policies in place can be found in the table below:
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |         Yes         | 40.122.30.120
| Web-1    |         No          | 10.0.0.4             |
| Web-2    |         No          | 10.0.0.4             |
| Elk-New-Server  |         No          | 10.0.0.4             |



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- The main advantage of automating configuration with Ansible is that it allows for accuracy and minimize errors and software can be updated to the most current version allowing for high availability of the network. 

The playbook implements the following tasks:
- The Ansible Playbook allows for automation of the different functions of the Elk Stack Server 
- Docker install via Ansible Playbook allows for the containers and machines to work cohesively
- Downloading the images allows for the creation of containers 

The following screenshot displays the result of running `docker ps -a` after successfully configuring the ELK instance:

https://github.com/cypachebot/Elk-Stack-Machine/blob/main/docker_ps_output.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 IP 10.0.0.9
- Web-2 IP 10.0.0.8

We have installed the following Beats on these machines:
- Beats packet elasticsearch-7.6.2-amd64.deb

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file to the Elk virtual machine.
- Update the hosts file to include servers Web-1 IP 10.0.0.9 & Web-2 IP 10.0.0.8
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
