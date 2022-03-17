## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](/Images/Project%20one%20Network%20Diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - List of Playbooks

    - [install-elk.yml](https://github.com/Djack06/Project-1/blob/main/install-elk.yml)
 
    - [filebeat.playbook.yml](https://github.com/Djack06/Project-1/blob/main/filebeat.playbook.yml)

    - [metricbeat-playbook.yml](https://github.com/Djack06/Project-1/blob/main/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly <ins>available</ins>, in addition to restricting <ins>access</ins> to the network.
- _TODO: What aspect of security do load balancers protect?_ <ins>Load balancers lets you evenly distribute network traffic to prevent failure caused by overloading a particular resource. They also defend an organization against distributed denial-of-service (DDos) attacks.</ins>

- _What is the advantage of a jump box?_ <ins>Jump boxes improve security because they are highly-secured computers which are never used for non-administrative tasks such as accessing email and internet browsing.</ins>

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the <ins>file system</ins> and system <ins>performance such as CPU usage and memory usage.</ins>
- _TODO: What does Filebeat watch for?_ <ins>Filebeat monitors log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.</ins>

- _TODO: What does Metricbeat record?_ <ins> Metricbeat collects metrics from the operating system and from services running on the server and ships them to the output you specifcy, such as Elasticsearch or Logstash.</ins>

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function | IP Address | Operating System |
|----------------------|----------|------------|------------------|
| Jump Box             | Gateway  | 10.0.0.4   | Linux/Ubuntu     |
| Web-1                | Server   | 10.0.0.9   | Linux/Ubuntu     |
| Web-2                | Server   | 10.0.0.10  | Linux/Ubuntu     |
| Project-1-Elk-Server | Server   | 10.1.0.4   | Linux/Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the <ins>JumpBox</ins> machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ <ins>Public IP Address: Personal/Public IP</ins>

Machines within the network can only be accessed by <ins>SSH</ins>.
- _TODO: Which machine did you allow to access your ELK VM?_ <ins>The JumpBox VM is the only machine allow to access the ELK VM.</ins> What was its IP address?_ <ins>10.0.0.4</ins>

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump Box             | No                  | Personal/Public IP   |
| Web-1                | No                  | 10.0.0.9             |
| Web-2                | No                  | 10.0.0.10            |
| Project-1-Elk-Server | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
<ins>Advantages to using Ansible are no special coding skills are required to use Ansible's playbooks.  It's flexible in that you can orchestrate the entire application environment no matter where it's deployed.</ins>

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...Install Docker
- ...Install Python3-pip
- ...Install Docker Module
- ...Increase virtual memory & configure system to use more memory
- ...Download and launch a docker elk container & enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker](/Images/Docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.9)
- Web-2 (10.0.0.10)

We have installed the following Beats on these machines:
- Project-1-Elk-Server, Web-1, Web-2

These Beats allow us to collect the following information from each machine:
- Filebeats collects log events such as logins.
- Metricbeat collects metric data from the operating system and from services such as Apache.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _elk_install.yml_ file to _/etc/ansible/elk_install.yml_.

- Update the _/etc/ansible/hosts_ file to include the following:
  - [elk]
  - 10.1.0.4 ansible_python_interpreter=/usr/bin/python3
 
- Run the playbook, and navigate to _http://[your_elk_server_ip]:5601/app/kibana_ to check that the installation worked as expected.



_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
