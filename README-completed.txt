## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
What aspect of security do load balancers protect? Web traffic/security against unauthorized users

What is the advantage of a jump box? Serves as a security hardened entry point to other VM(s) in your network, only allowing connections from the jumpbox. The jumpbox helps prevent infecting other servers in the network.   

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs. 
- _TODO: What does Filebeat watch for? Filebeat keeps track of log data from sources then collects those events and forwards them to Elasticsearch or Logstash.
- _TODO: What does Metricbeat record? Metricbeat is a type of type responsible for collecting metrics from sources, which can be systems and services, and understands how to process those metrics and put them into a specific format that is later forwarded to Elasticsearch.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

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
| Web1 & 2 | No                  |                      |
|ELK-Server| No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time and reduces the chances of syntax errors in the deployment process. Another advantage is by using a single playbook, it allows us to automate the creation of multiple servers. 
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Configure ELK-VM with Docker: specifies the user and machine
- Install docker.io: installs the containerization software
- Install pip3: software that supports the installation and management for additional modules
- Install Docker python module: installs docker basic modules from previous python module (pip)
- Increase virtual memory: allows us to use more memory, if need be
- Download and launch a docker elk container: ELK docker container gets downloaded; specific published ports --> 5601:5601, 9200:9200, 5044:5044


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring:
- Web 1 10.0.0.8
- Web 2 10.0.0.9

We have installed the following Beats on these machines:
Specify which Beats you successfully installed: Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat monitors and collects log files and events in locations specified. For example, when configuring Filebeat, you can input that all files in directory /etc/hosts/ ending in *.txt will be harvested. 
Metricbeat helps us monitor/gather metrics and stats in our servers such as memory or CPU usage. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/roles
- Update the filebeat-config.yml file to include my ELK server's IP address.

- Run the playbook, and navigate to http://52.160.124.7:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks: 
- _Which file is the playbook? Where do you copy it? /etc/ansible/files/filebeat-config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? You update filebeat-config.yml. Updating the host file with the particular IP addresses then including on either websevers or elk server, or whichever machine created. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.160.124.7:5601/app/kibana





_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._













