# Elk-Project
Within this project it demonstrated where metric and file beats are downloaded within a virtual machine called ELK on Azure lab services
 (These playbooks can be found in the file section) 
 - Filebeat Playbook
 - Metric Playbook 
 - Elk Playbook 
 


This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available , in addition to restricting inbound traffic to the network.

The aspect of security of load balancers is to protect against distubed denial-of-service attack otherwise known as DDoS attack, while simultaneously offloading traffic from one provider to another. This will allow the HTTP traffic to flow smoothly through webservers without too many user requests. The way this works is that the traffic that is attacked is shifted from a corporate server to a cloud provider. The advanatge of a jump box is that it allows a user to use a network system through a specific IP address. 



Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network files and system monitor system metrics.

- Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.


What does Metricbeat record?

- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache. HAProxy.




Access Policies



The machines on the internal network are not exposed to the public Internet.
Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My personal IP address 

A connection to the Jumpbox will allow an SSH to Web 1,2,3, and the Elk Server. The IP address 51.12.241.212.

Elk Configuration



Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible is completely free. With the automatic configuration processes the configuration of multiple webservers within one shot. Patches can also be made easily to fix the ansible-playbooks. 


What is the main advantage of automating configuration with Ansible?


Very simple to set up and use: No special coding skills are necessary to use Ansible's playbooks (more on playbooks later). Powerful: Ansible lets you model even highly complex IT workflows. Flexible: You can orchestrate the entire application environment no matter where it's deployed

The playbook implements the following tasks:

Identifies the target machines
Installs docker.io
Installs pip3 (python3) 
Install Docker Python Module
System Control initated to increase virtual memory on the target machines (DVWAs)
Launching the Docker Container with Restart Enabled
Ensuring the correct Ports are enabled (5601, 9200, 5044)

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.
 sudo docker ps 


Target Machines & Beats
This ELK server is configured to monitor the following machines:

We have installed the following Beats on these machines:

10.4.0.9
10.4.0.10
10.4.0.11


These Beats allow us to collect the following information from each machine:
- Filebeats 
- Metricbeats 

- Filebeats collects data of the filesystem and changes (such as weblog data) 
- Metricbeats detects changes in system metrics (such as look for SSH attempts) 


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

- Copy the configuration file to your Web VMs from your Ansible container.
- Update the hosts file to include the IP addresses for Web and Elk servers
- Run the playbook, and navigate to http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected.



Which file is the playbook? Where do you copy it?


- The Filebeat configuration and copy it to copy /etc/ansible/filebeat-config.yml to /etc/filebeat/filebeat.yml

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?


- update filebeat-config.yml
- Find a specific machine to install by going into the host files and updating the ip addressses of the web and elk servers for the ansible containers to run on 

Which URL do you navigate to in order to check that the ELK server is running?
- http://[your.ELK-VM.External.IP]:5601/app/kibana.

Specific commands the user will need to run to download the playbook and update the files.

- git clone 
- git add 
- git commit -m "VersionX.X"
- git push









