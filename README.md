 ### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
https://github.com/HDRider1/HDBOX/blob/main/Diagrams/diagram2%20.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible  file may be used to install only certain pieces of it, such as Filebeat.
https://github.com/HDRider1/HDBOX/blob/main/Ansible/Filebeat

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
- Load balancers can protect systems against DDos attacks. The advantage of a jump box is having the 
  ability to SSH into a virtual machine and containers with hardened security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the  logs and system traffic .
- Filebeat monitors multiple logs depending on the area specified.
- Metricbeat records the statistics from the servers.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WEB1     |Webserver | 10.0.0.6   | Linux            |
| WEB2     |Webserver | 10.0.0.7   | Linux            |
| ELk Host |Webserver | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner  machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 	20.120.119.10

Machines within the network can only be accessed by Jump Box Provisioner .
- 	I allowed my Jump Box Provisioner to access my Elk Host. The IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|---------- |---------------------|----------------------|
| Jump Box  | No                  | 20.120.119.10        |
|Web1 Docker| No                  |  10.0.0.4            |
|Web1 Docker| No                  |  10.0.0.4            |
| Elk Host  | No                  |  10.0.0.4            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- •	Ansible allows users to save time when their daily tasks are automated.

The playbook implements the following tasks:
- 	Installs Docker
-   Installs python3-pip
-   Installs Docker python module
-   Sets the vm.max_map_count to 262144
-   Downloads and launches a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Untitled1](https://user-images.githubusercontent.com/89166484/146654026-c8e799fb-4ba0-4a95-a44c-1aeaaa9e769b.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
1	Web1 10.0.0.6
2	Web2 10.0.0.7
3	Elk Host 10.1.0.4


We have installed the following Beats on these machines:   
•	FileBeat
•	MetricBeat

These Beats allow us to collect the following information from each machine:
-	File Beat monitors log files and collects log events from specific locations such as the unique visitors’ logs. Metric beat records the statistics from the operation system running on the server such as how much RAM or CPU was being used at a specific time.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
-	Copy the filebeat-config.yml file to /etc/ansible/filebeat-config.yml.
-	Update the filebeat-config.yml file to include the IP address of the Elk Machine.
- Run the playbook, and navigate to4	http://[Your IP ( my it always different ) ]:5601/app/kibana to check that the installation worked as expected.

- new-playbook.yml is the playbook file and it is copied to Web1 and Web2 .
- You will need to update the hosts file to make Ansible run the playbook on a specific machine. You will need to list 10.1.0.4 ansible_python_interpreter=/usr/bin/python3 to     install the ELK server on and specify the IP addresses of Web1 and Web2 VMs to install FileBeat on.
-	I navigated to http://168.61.190.18:5601/app/kibana#/home in order to check that the ELK server is running.
 ### Bonus
 - ansible-playbook
