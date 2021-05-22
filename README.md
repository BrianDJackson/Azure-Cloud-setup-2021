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
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/BrianDJackson/IT-Security-Class-2021/blob/main/Docker%20running%20Elk%20Screenshot.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._


