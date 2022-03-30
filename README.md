## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Network Diagram](https://github.com/Kara-Hambrick/Elk-Stack-Project/blob/main/Diagrams/Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  [elk-install.yml](https://github.com/Kara-Hambrick/Elk-Stack-Project/blob/main/Ansible/elk-install.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? 
Load Balancers create an even distribution of network traffic which in return allows a more reliable and larger capacity of applications. 
- What is the advantage of a jump box?_
A jump box serves as an initial point of contact that users connect to before gaining access to any adminstrative tasks. The jump box is more secure and easibly monitorable.   
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network traffic and system files.
- What does Filebeat watch for?
Logs and system file changes. 
- What does Metricbeat record?
Metrics and statistic data

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|----------  |------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| DVWA 1   | Web Server | 10.0.0.5   | Linux            |
| DVWA 2   | Web Server | 10.0.0.6   | Linux            |
| Elk      | Web Server | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 71.80.108.169

Machines within the network can only be accessed by one another.
- Only the DVWA 1 and DVWA 2 can access the ELK server. 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 71.80.108.169        |
| ELK      | No                  | 10.0.0.4             |
| DVWA 1   | No                  | 10.0.0.4,10.0.0.6    |
| DVWA 2   | No                  | 10.0.0.4, 10.0.0.5   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It allowed the effeciency of automation (easier to read and update) as well as it is cost effective. 

The playbook implements the following tasks:
- Increase memory
- Install docker.io
- Install pip3
- Install docker python module
- Launch docker container


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA 1 & DVWA 2 VMs

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat
- Packetbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbooks to the Ansible Control Node.
- Update the host file to include the Elk server. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? 
install_elk.yml
install_filebeat.yml
install_metricbeat.yml
- Where do you copy it?
/etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? 
metricbeat-configuration.yml
filebeat-configuration.yml
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
