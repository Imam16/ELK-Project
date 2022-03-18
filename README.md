# ELK-Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/Network ELK.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? The load balancers help in assuring the availability of our machiens by stabilizing the load each virtual machien recives. The jump box gives us an additional layer of security by exposing one Virtual Machine to the internet instead of two.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system settings.
- What does Filebeat watch for? Watches for changes in log files and ships them when changes are detected
- What does Metricbeat record? It records the hosts metrics and ships them

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WEB1     | DVWA     | 10.0.0.5   | Linux            |
| WEB2     | DVWA     | 10.0.0.6   | Linux            |
| ELKVM    | ELK      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 41.87.74.2

Machines within the network can only be accessed by the jumpbox.
-Jump Box 10.0.0.4 through port 22 (SSH) 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 41.87.74.2           |
| WEB1     | No                  | 10.0.0.4             |
| WEB2     | No                  | 10.0.0.4             |
| ELKVM    | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It saves alot of time by automating the commands instead of inputing them one at a time on the command line. 

The playbook implements the following tasks:
- ... Install docker.io using the apt module
- ... Use pip to install the docker module
- ... Increase the virtual memory usage by running sysctl 
- ... Download the elk docker container by specifying the image and port. Also list the published ports that ELK will run on
- ... Make sure to enable the docker service on boot using systemd

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- WEB1: 10.0.0.5 WEB2: 10.0.0.6

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
-  Filebeat collects log file logs from machinces. For example, collecting logs from /log/syslog that shows a python command was run. Metricbeat collects the machines metrics such as host machine names or OS versions.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-config.yml file to the target machine.
- Update the Filebeat-config file to include the ELK's IP address and ports that it will use.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Question and Answers
- Which file is the playbook? Where do you copy it? The file is called playbook.yml and you can copy it here
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ You should update the ansible hosts file to specify machinces. We specify using host groups, ELK contains the IP address for the ELK machince will Webservers has WEB1 and WEB2
- What URL do you navigate to check the ELK server? Navigate to http://[ElkVM IP address]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
