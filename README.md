# cybersecurity-bootcamp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![AzureELKDiagramDonella](https://user-images.githubusercontent.com/80011567/122502103-f7544700-cfc3-11eb-9b1d-39d960d61f6c.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  (../Ansible/install-elk.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting in-bound access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.

The configuration details of each machine may be found below.

| Name                 | Function   | IP Address | Operating System |
|----------------------|------------|------------|------------------|
| Jump-Box-Provisioner | Gateway    | 10.0.0.4   | Linux            |
| Web-1                | Webserver  | 10.0.0.5   | Linux            |
| Web-2                | Webserver  | 10.0.0.6   | Linux            |
| DVWA-VM3             | Webserver  | 10.0.0.11  | Linux            |
| ELK-VM               | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.183.111.176

Machines within the network can only be accessed by my jump box provisioner.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 75.183.111.176       |
| Web-1                | No                  | 10.0.0.4             |
| Web-2                | No                  | 10.0.0.4             |
| DVWA-VM3             | No                  | 10.0.0.4             |
| ELK-VM               | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it frees up time for more important tasks.

The playbook implements the following tasks:
- Increases the max useable memory
- Installs docker.io
- Installs pip3
- Installs the python docker module
- Downloads and launches a docker web container
- Enables the docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/80011567/122502046-d986e200-cfc3-11eb-99ae-515a683e1d96.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.11

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data on the file system, such as an audit log.
- Metricbeat collects data on machine metrics, such as uptime.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible control node.
- Update the hosts file to include webservers and elk IP groups. 
- Run the playbook, and navigate to (http://[host ip]/app/kibana#/home) to check that the installation worked as expected.
