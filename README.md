## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(https://github.com/Abagira/Bootcamp_Project_1/blob/main/Diagram/VmNetworkDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  -  my-elkservers.yml
  -  filebeat_install.yml
  -  metricbeat_install.yml

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
Load balancers protect from DDoS attack. Jumpbox is a network system that gives user access and manage devices from single node.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
- Filebeat monitors the changes of the information in the file and when it has been effected.
-  Metricbeat collects metrics and statistics from the servers and send them to the respective output

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| DVWA-Web1| Server   | 10.0.0.6   | Linux            |
| DVWA-Web2| Server   | 10.0.0.7   | Linux            |
| DVWA-Web3| Server   | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 Add whitelisted IP addresses_Home public IP addresses

Machines within the network can only be accessed by Jumpbox.
-Which machine did you allow to access your ELK VM? What was its IP address?_ Jump box server and it has an IP address of 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|---------- |---------------------|----------------------|
| Jump Box  |  Yes                |  Home IP             |
| DVWA-Web1 |  No                 |  10.0.0.5            |
| DVWA-Web2 |  No                 |  10.0.0.5            |
|DVWA-Web3  |  No                 |  10.0.0.5            |
|Elk Servers|  No                 |  10.0.0.5            |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-: What is the main advantage of automating configuration with Ansible?_
         It allows the user to run commands into different servers from a single playbook
The playbook implements the following tasks:
- : In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install: docker.io
- Install: python.pip
- Install: docker
- Command: sysctl -w vm.max_map_count=262144
- Launch docker container: elk

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- : List the IP addresses of the machines you are monitoring_
DVWA-Web 1= 10.0.0.6
DVWA-Web 2= 10.0.0.7
DVWA-Web 3= 10.0.0.8
We have installed the following Beats on these machines:
- : Specify which Beats you successfully installed_
     Metricbeat and filebeat
These Beats allow us to collect the following information from each machine:
- : In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
    Metricbeat collects statistics that is Images/Metricbeat while Filebeat collects the changes done that is Images/Filebeat

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk_install.yml file to /etc/ansible/roles/elk_install.yml
- Update the hosts file to include Ips destination and elk.
- Run the playbook, and navigate  to check that the installation worked as expected.

- The playbook is /filebeat-configuration.yml and  copies to /etc/ansible/
- Edit the /etc/ansible/host file to add webserver/elkserver ip addresses
- Naviagte through http://elkserver-ip:5601/app/kibana to check the installation of elk server

