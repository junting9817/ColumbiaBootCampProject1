## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network_Diagram](https://user-images.githubusercontent.com/78493101/118381325-d741fa00-b5b7-11eb-868b-cd1dfb611d04.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?
  - Redundancy
  - Jump box provides enhanced security for the network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- What does Filebeat watch for?
  - Changes in system files
- What does Metricbeat record?
  - Metrics from the systems and services on the server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.6   | Linux            |
|  Web-1   | Webserver| 10.0.0.7   | Linux            |
|  Web-2   | Webserver| 10.0.0.8   | Linux            |
|ELK-server|Monitoring| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box-provisional machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 96.234.46.214

Machines within the network can only be accessed by the jump-box-provisional.
- Which machine did you allow to access your ELK VM? What was its IP address?
  - Personal Machine: 96.234.46.214

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |         Yes         |    96.234.46.214     |
|  Web-1   |         No          |      10.1.0.4        |
|  Web-2   |         No          |      10.1.0.4        |
|ELK-server|         Yes         |    96.234.46.214     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  - It can be simply set up to multiple machines

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
  - Increase memory
  - Install docker.io, pip3, and Docker python module
  - Downloaad and launch a docker elk container
  - Enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img width="917" alt="ELK_Docker_PS" src="https://user-images.githubusercontent.com/78493101/118381334-ef197e00-b5b7-11eb-8762-81a1a0ebb7f1.png">


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring
  - 10.0.0.7
  - 10.0.0.8

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed
  - Filebeat
  - Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
  - Filebeat collects data related to the file system, and the Metricbeat collects data about machine metrics. For example, in the case of the Metricbeat, we can expect to see the usage metrics about CPU and memory.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible folder.
- Update the playbook file to include [webservers] and [elkservers]
- Run the playbook, and navigate to http://23.101.194.86:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? 
  - Files ending with .yml
  - Container
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  - Host file
  - [webservers] and [elkservers]
- _Which URL do you navigate to in order to check that the ELK server is running?
  - http://23.101.194.86:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
