Automated Elastic Stack Deployment

The files in this repository were used to configure the network depicted below.

<img src="Diagrams/NetworkDiagram.png" title="topolgydiagram" alt="topolgydiagram" width="600" height="700">

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ElkStack file may be used to install only certain pieces of it, such as Filebeat.

FileBeat-Config:.
This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting overloads to the network.

Load balancers defend organizations against DDos attacks by shifting attack traffic away from the corporate server towards a public cloud.   A jump box provides a buffer by being an origination point for admins running tasks.  Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches and monitors log files for anomalies and sends data to pre determined location for review.
Metricbeat is installed on the server and monitors operating system changes.
The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

| Name	  | Function	| IP Address	| Operating System
|-------- |:---------:| :----------:|-----------------:|
|Jump Box	| Gateway	  |  10.0.0.4	  |       Linux      |
|Web 1		| Virtual Machine | 10.0.0.5 | Linux | 
|Web 2		|	Virtual Machine | 10.0.0.7 | Linux |
|ElkStack	|	Virtual Machine | 10.1.0.4 | Linux |

Access Policies:

The machines on the internal network are not exposed to the public Internet.

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 136.35.21.76 and 140.82.173.162


Machines within the network can only be accessed by SSH.

The ElkStackVM can access at IP address 40.75.18.92
A summary of the access policies in place can be found in the table below.


| Name	| Publicly Accessible	 | Allowed IP Addresses
| ------| :------------------: | -------------------: |
| JumpBoxProvisioner	| Yes      |  52.146.40.102
|ElkStackVM | No     |     40.75.18.92    |
|Web 1      | No     | 10.0.0.5    |
|Web 2      | No     | 10.0.0.7    |

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

It allows admins to automate monotonous tasks to free time for more important items.
The playbook implements the following tasks:

Steps of the ELK installation play. 
* Navigate into jumpbox through SSH 
* curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
* sudo apt-get update
* sudo apt-get install -y docker-ce
* Confirm the docker is running by running code: sudo systemctl status docker
* Copy and run this playbook: Ansible/Docker-Compose.docx  



The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

TODO: Update the path with the name of your screenshot of docker ps output

Target Machines & Beats

This ELK server is configured to monitor the following machines:

We have installed the following Beats on these machines:
Containers being monitored by beats:
* DVWA 1 IP: 10.0.0.7
* DVWA 2 IP: 10.0.0.8

These Beats allow us to collect the following information from each machine:
* Filebeat- This beat allows us to collect information about the file system.
* Metricbeat- This beat collects data about machine metrics.

Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: JumpBoxProvisioner is utilized

SSH into the control node and follow the steps below:

Copy the playbook file to Ansible control node.
Update the elk-stack file to include...
Run the playbook, and navigate to container to check that the installation worked as expected.


* Install_elk.yml playbook file
* The playbook needs to be copied to the host folder on the target machine
* You must create a 'hosts' file on the specific machine you want to run the file on 
* The playbook for the elk is different than the one for filebeat which identifies which program is running ojn which machine.
* Curl http://10.0.0.8:5601 which is the address for kibana to confirm if it is working correctly.
* As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
