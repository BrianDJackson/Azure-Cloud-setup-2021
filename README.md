## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/BrianDJackson/IT-Security-Class-2021/blob/main/AzureCloudDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible Playbook file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/BrianDJackson/IT-Security-Class-2021/blob/main/filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient and reliable, in addition to restricting unwanted access to the network.
- The load balancers reduce the possibility of a network being overwhelmed by incoming traffic. This can help to protect the network from Distributed denial of service (DDOS) attacks. Using a Jump Box makes the VMs less vulnerable to attack because the VMs are only accessed through the Jump Box via ssh. The VMs are set to prevent access using an external IP address. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system files.
- Filebeat monitors the log files or locations according to settings then collects logs and send them to Elasticsearch or Logstash for further data analysis.
- Metricbeat collects metrics from the operating system and services running on a server. 


| Name     | Function           | IP Address    | Operating System |
|----------|--------------------|---------------|------------------|
| Jump Box | Gateway            | 40.121.64.159 | Linux/Ubuntu     |
| Web-1    | Webserver          | 10.0.0.5      | Linux/Ubuntu     |
| Web-2    | Webserver          | 10.0.0.6      | Linux/Ubuntu     |
| Web-3    | Webserver          | 10.0.0.7      | Linux/Ubuntu     |
| ELK-VM   | Logging/Monitoring | 10.1.0.4      | Linux/Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address:
-	69.169.8.120

Machines within the network can only be accessed by the IP address assigned to the Jump Box.
- The Jump Box is able to access the ELK VM using IP address:
  - 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses   |
|---------------|---------------------|------------------------|
| Jump Box      | Yes                 | 40.121.64.159          |
| Load Balancer | Yes                 | 40.114.90.80           |
| Web-1         | No                  | 10.0.0.5               |
| Web-2         | No                  | 10.0.0.6               |
| Web-3         | No                  | 10.0.0.7               |
| ELK-VM        | Yes                 | 10.1.0.4, 20.97.22.134 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because allows for building infrastructure quickly.  

The playbook implements the following tasks:
-	Install Docker
-	Install Python3-pip
-	Download and launch the DVWA web container
-	Enable Docker service upon every reboot


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img width="422" alt="Docker running Elk Screenshot" src="https://user-images.githubusercontent.com/77516651/119247219-ce23d080-bb55-11eb-85f8-f3e99a394583.PNG">



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 - 10.0.0.5
 - 10.0.0.6
 - 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeats collects logs which can be used to analyze network traffic. 
- Metricbeat collects system data and memory statistics for monitoring.
Using these tools we would hope to monitor logs and services running on the server to detect any suspicious network traffic. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- From the Jump Box connect to the Ansible container within the Jump Box.
- Create a YAML playbook file then update the /etc/ansible/ansible.cfg file to include the remote user name being used for all virtual machines on the network.
- Run the YAML playbook and make corrections if any errors occur while running the playbook. 
- After successfully running the playbook, SSH into your new Ansible container to ensure that it functions.  


The Playbooks are the YAML files that end with the extension .yml.
Playbooks can be copied from this file: https://github.com/BrianDJackson/IT-Security-Class-2021/tree/main/Ansible/Ansible

- The /etc/ansible/hosts file needs to be updated to make Ansible run the playbook on a specific machines. Those machines IP addresses need to be added to the hosts file. 

 - Make sure that your ELK server is installed on a machine that does not contain a webserver. Filebeat needs to be installed on all machines with webservers because Filebeat is going to send logs from your webservers to be analyzed using the ELK server. Your network should be constructed in this manner so the ELK machine can monitor on an independent server. 

The final step is to test then use Kibana to monitor network traffic.
- Input http://[your.VM.IP]:5601/app/kibana to access your ELK Stack. 
