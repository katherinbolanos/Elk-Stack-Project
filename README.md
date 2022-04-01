# Elk-Stack-Project

The files in this repository were used to configure the network depicted below.

![Untitled Diagram drawio](https://user-images.githubusercontent.com/102314477/161353411-10a5b4d0-6ed1-4d9a-8206-1bcb0164415a.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effective, in addition to restricting access to the network.
What aspect of security do load balancers protect? Web traffic/security against unauthorized users, prohibit communication from malicious IP addresses, support security configurations within networks. 

What is the advantage of a jump box? Serves as a security hardened entry point to other VM(s) in your network, only allowing connections from the jumpbox. The jumpbox helps prevent infecting other servers in the network.   

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs. 

What does FileBeat watch for? Filebeat helps keep log data organized through forwarding and centralizing the information specified- which once forwarded to Elasticsearch or Logstash, used for indexing. 

What does Metricbeat record? Monitors and collects data/metric from the OS being used.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.7   | Linux            |
| Web-1    | Webserver| 10.0.0.8   | Linux            |
| Web-2    | Webserver| 10.0.0.9   | Linux            |
|ELK-Server|Elk-server| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
99.184.129.176

Machines within the network can only be accessed by Jump-Box-Provisioner.
Which machine did you allow to access your ELK VM? Jump-Box-Provisioner
What was its IP address? 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 99.184.129.176:22    |
| Web1 & 2 | No                  | 10.0.0.8/10.0.0.9    |
|ELK-Server| No                  | 99.184.129.176:5601  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time and reduces the chances of syntax errors in the deployment process. Another advantage is by using a single playbook, it allows us to automate the creation of multiple servers. 

What is the main advantage of automating configuration with Ansible? Ansible allows you to create tasks required to be done within playbooks to then be deployed to the required systems needed to be ran specifically how needed to be ran. 

The playbook implements the following tasks:

- Configure ELK-VM with Docker: specifies the user and machine
- Install docker.io: installs the containerization software
- Install pip3: software that supports the installation and management for additional modules
- Install Docker python module: installs docker basic modules from previous python module (pip)
- Increase virtual memory: allows us to use more memory, if need be
- Download and launch a docker elk container: ELK docker container gets downloaded; specific published ports --> 5601:5601, 9200:9200, 5044:5044


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps output](https://user-images.githubusercontent.com/102314477/161354115-3923f108-153d-49eb-b717-c09f6b71db4d.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring:
- Web 1 10.0.0.8
- Web 2 10.0.0.9

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat monitors and collects log files and events in locations specified. For example, when configuring Filebeat, you can input that all files in directory /etc/hosts/ ending in *.txt will be harvested. 
Metricbeat helps us monitor/gather metrics and stats in our servers such as memory or CPU usage

### Using the Playbook

Steps to verifying that Filebeat and Metricbeat are operating as they were configured to do so:

- Copy the filebeat-playbook.yml file to /etc/ansible/roles
- Update the filebeat-config.yml file to include my ELK server's IP address.
-
- Which file is the playbook? Where do you copy it? /etc/ansible/files/filebeat-config.yml
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? You update filebeat-config.yml. Updating the host file with the particular IP addresses then including on either websevers or elk server, or whichever machine created. 
- Which URL do you navigate to in order to check that the ELK server is running? http://52.160.124.7:5601/app/kibana



