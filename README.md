## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network. Load balancers protect the servers from inbound traffic. It balances the incoming traffic to the available servers to assure availability. 

The advantage of the jump box is to be a security measure to have only one access point into the network. It is a hardened device that only allows our workstation to access the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files in the Virtual Machines within the network and watch system metrics.Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Filebeat monitors the log files for specified locations, collects log events, and forwards them to the ELK Stack.
Metricbeat takes the metrics and statistics that it collects and sends them to the ELK Stack.

The configuration details of each machine may be found below.


| Name               | Function   | IP Address | Operating System |
|--------------------|------------|------------|------------------|
| Jump Box           | Gateway    | 10.0.0.4   | Linux            |
| Web-1              | Web Server | 10.0.0.7   | Linux            |
| Web-2              | Web Server | 10.0.0.6   | Linux            |
| ELK-Server-Machine | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 73.240.160.82


Machines within the network can only be accessed by the other machines within the network. The Elk-Stack is allowed access from Web-1 and Web-2. 

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  | Yes                 | 73.240.160.82        |
| Web-1     | No                  | 10.0.0.0/24          |
| Web-2     | No                  | 10.0.0.0/24          |
| ELK-Stack | No                  | 10.0.0.0/24          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because there is less chance for human error. It is also more efficient to redeploy the architecture in other environments.

The playbook implements the following tasks:
- Download and install filebeat and metricbeat file
- Enable and Configure System
- Start filebeat and metricbeat service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web-1 and Web-2 at the IP addresses 10.0.0.6 and 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat detects changes to the filesystem.
- Metricbeat collects metrics from the system and services. It collects metrics for CPU, memory, Redis, NGINX, and others.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible control node.
- Update the hosts file to include Groups and IPs
- Run the playbook, and navigate to Kibana (http://20.211.105.234:5601/) to check that the installation worked as expected.



