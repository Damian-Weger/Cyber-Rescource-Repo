<<<<<<< HEAD
\## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

# ~/Cyber-Resource_Repo/Images/Network_Diagrams/elk_diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-config.yml file may be used to install only certain pieces of it, such as Filebeat.

  - install-ELK.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient and responsive to users, in addition to restricting unwanted access to the network.
- load balancer distributes incoming traffic among multiple VMs making it diffulcult for Denial of Service attacks. The advantage for using one is that it is a hardened and monitored device that spans two different security zones providing a controlled means of access between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the applications and system servers.
- Filebeat collects, parse and visualize ELK logs in a single command.
- Metricbeat collects metrics from the system and services running on the server.

The configuration details of each machine may be found below.

|   Name   | Function | IP Address | Operating System |   |
|:--------:|:--------:|:----------:|:----------------:|---|
| Jump Box | Ansible  | 10.1.0.4   | Linux            |   |
| Web-1    | DVWA     | 10.1.0.5   | Linux            |   |
| Web-2    | DVWA     | 10.1.0.6   | Linux            |   |
| Web-3    | ELK      | 10.1.0.9   | Linux            |   |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 66.67.73.6

Machines within the network can only be accessed by Jump Box.
- Only the Jump Box has permission to connect to the ELK VM. Its ip address is 10.1.0.4

A summary of the access policies in place can be found in the table below.
|   Name   | Publicly Accessible | Allowed IP Addresses |
|:--------:|:-------------------:|:--------------------:|
| Jump Box | Yes                 | 10.1.0.5 10.1.0.6    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The primary benefit of Ansible is it allows IT administrators to automate away the drudgery from their daily tasks. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
- ... Install Python3-pip
- ... Install Docker using pip
- ... Intall ELK
- ... Enable docker service on restart


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5, 10.1.0.6, 10.1.0.9

We have installed the following Beats on these machines:
- ... Filebeat
- ... Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat and metricbeat playbook file(s) to the ansible contianer.
- Update the config file to include the ELK's IP address
- Run the playbook, and navigate to http://52.183.107:5601/app/kibana to check that the installation worked as expected.

