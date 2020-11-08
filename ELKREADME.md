## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!images/RedTeam_Elk_Map.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: elkinstall.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive to requests, in addition to restricting traffic to the network. Load balancers help allocate available resources to where they are needed most to help prevent a server from going down due to a DDoS attack. The advantge of using a JumpBox is that you can dramatically lower the number of systems you have that are exposed to the outside internet. If you have a JumpBox, you can configure this VM to have very secure permissions for access, and hte rest of the network can only be accessible via the JumpBox.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system settings.
-  FileBeat monitors the log files and forwards them to an elastic search for logging
- MetricBeat that collects metrics from an operating server and can ship them to an output function.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
|Follower1 | DWVA     | 10.0.0.5   | Linux            |
|Follower3 | DWVA     | 10.0.0.7   | Linux            |
|Follower5 | DWVA     | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:My Home Computer's IP address

Machines within the network can only be accessed by The JumpBox. This includes the Elk Server.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | my home IP address   |
|Followers | No                  | Jump Box PIP 10.0.0.4|
| ELK      | Yes                 |Port 5601, JumpBox    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is very scalable. Instead of manually installing on each machine, you can automate the Ansible container to install as many pieces of software you want on as many machines as you want.

The playbook implements the following tasks:
- Configures the server to have an incraesed memory amount
- Installs Docker.io, which downloads the software for docker
- Installs python-pip, which allows you to install and maange software packages in python
- installs Docker, which uses docker.io to set up docker which delivers software into containers

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Screenshot/ConfiguredElk

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- It monitors the 3 Followers in the previous, so 10.0.0.5,7,8

We have installed the following Beats on these machines:
- MetricBeat and FileBeat

These Beats allow us to collect the following information from each machine:
- FileBeat monitors the log files and forwards them to an elastic search for logging.
- MetricBeat that collects metrics from an operating server and can ship them to an output function.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible container.
- Update the hosts file to include the IP addresses of the servers you want to configure.
- Run the playbook, and navigate to ELK server or the Kibana website to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- All of the playbooks end in .yml. The playbooks are in the installymls folder.
- You update the hosts file. In the hosts file, you can configure which groups of machines you want to run the playbook on.
- YourIP:5601

