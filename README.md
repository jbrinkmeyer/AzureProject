## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  
![](AzureProject/Diagrams/ELK.PNG "Elk Diagram")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ReadMe file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
What aspect of security do load balancers protect? Load balancers protect the reliability acces of security. What is the advantage of a jump box? You are able to restric access to the virtual machines through a single entry point.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system resources.
What does Filebeat watch for? Discrepancies in log data. 
What does Metricbeat record? Discrepancies in system resources and running processes.

The configuration details of each machine may be found below.

| Name     | Function      | IP Address    | Operating System |
|----------|---------------|---------------|------------------|
| Jump Box | Gateway       | 10.0.0.1      | Linux            |
| Web-1    | DVWA Container| 10.0.0.5      | Linux            |
| Web-2    | DVWA Container| 10.0.0.6      | Linux            |
| Elk-VM   | Elk Container | 40.65.226.160 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
whitelisted IP addresses My Personal Computer IP

Machines within the network can only be accessed by the Jump Box Provisioner.
Which machine did you allow to access your ELK VM my personal computer? What was its IP address? 99.96.103.234

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 99.96.103.234        |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible? The machine can be recreated equally and updated easily.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
 - Increase memory available to the ELK box
 - Install docker.io
 - Install pip3
 - Install python docker module
 - Download and launch elk web container
 - Enable Docker Service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](AzureProject/Diagrams/docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5 Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
 - Filebeat monitors specified logfiles, collects events that occur and forewards them to Logstash.
 - Metricbeat collects metrics from the operating system and the services that are running on the server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to /etc/ansible.
- Update the hosts file to include:
  [elk] 
  10.1.0.4 ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to 40.65.226.160/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- _Which file is the playbook?filebeat-config.yml Where do you copy it?/etc/filebeat/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? filebeat-config.yml
- _Which URL do you navigate to in order to check that the ELK server is running? 40.65.226.160/app/kibana


