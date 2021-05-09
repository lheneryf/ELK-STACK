## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![project1](https://user-images.githubusercontent.com/8354230/117556547-fb816200-b01e-11eb-9c75-6e5069f62668.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk Deployment file may be used to install only certain pieces of it, such as Filebeat.

  
  [elksetup.yml](https://github.com/lheneryf/ELK-STACK/blob/main/elksetup.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
-Load balancers helps to protect from (DDOs) denial-of-service attacks by balancing the traffic between servers. 
- What is an advantage of using a jump box?- The jump box forces all the traffic through a single node. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat monitors the log files or locations that you specify, collects log events and then sends them to Elasticsearch. 
- Metricbeat collects data from operating systems and from servies running on servers periodically then forwards them over to Elasticsearch. 

The configuration details of each machine may be found below.

| NAME         | FUNTION | IP ADDRESS | OPERATING SYSTEM |
|--------------|---------|------------|------------------|
| Jump Box     | Gateway | 10.0.0.4   | Linux(Ubuntu)    |
| Web-1        | DVWA    | 10.0.0.5   | Linux(Ubuntu)    |
| Web-2        | DVWA    | 10.0.0.6   | Linux(Ubuntu)    |
| Web-3        | DVWA    | 10.0.0.7   | Linux(Ubuntu)    |
| ELK-STACK-VM | ELK     | 10.1.0.4   | Linux(Ubuntu)    |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Personal IP address

Machines within the network can only be accessed by SSH port 22.
- I allowed the docker container access to my Elk-Stack-VM the IP address is: 172.17.0.1

A summary of the access policies in place can be found in the table below.

| NAME         | Publicaly Accessible | Allowed IP Addresses |
|--------------|----------------------|----------------------|
| Jump Box     | NO                   | Personal IP          |
| Web-1        | NO                   | 172.17.0.1           |
| Web-2        | NO                   | 172.17.0.1           |
| Web-3        | NO                   | 172.17.0.1           |
| ELK-STACK-VM | NO                   | 172.17.0.1           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automating with ansible allows for multiple machines to be configured automatically running a playbook versus manual configuration on each machine. 

The playbook implements the following tasks:
- The header of the Playbook can specify different group of machines.
- The playbook should install services like docker.io, python3-pip and docker.
- Enables the servies after it has been run. 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![sudo docker ps](https://user-images.githubusercontent.com/8354230/117093771-c3c0a480-ad16-11eb-9b4f-4cbc96643285.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- WEB-1: 10.0.0.5, WEB-2: 10.0.0.7, WEB-3: 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat and Metricbeat.

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system it allows for monitoring of files for suspicious changes. Metricbeat collects machine metrics like the uptime and CPU usage it is a easy to collect information about machines in the network. _

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the [playbook](https://github.com/lheneryf/ELK-STACK/blob/main/filebeat-playbook.yml) file to ansible container []().
- Update the [hosts configuration](https://github.com/lheneryf/ELK-STACK/blob/main/hosts) file to include IP addresses. 
- Run the playbook, and navigate to the ELK-STACK-AM and web-1-3[]() to check that the installation worked as expected.
- Update the [Hosts](https://github.com/lheneryf/ELK-STACK/blob/main/hosts) file to specify what machines you want to install the filebeat and metricbeat on. 
- Which URL do you navigate to in order to check that the ELK server is running?
http://[your.VM.IP]:5601/app/kibana

The commands needed to run the Ansible configuration for the Elk-Server are:
SSH into jumpBox Vm ssh azadmin@13.77.176.12
Run sudo docker container list -a
Run sudo docker start container [Container name]
Run sudo docker attach container [Container name]
Update the hosts file in /etc/ansible/[hosts](https://github.com/lheneryf/ELK-STACK/blob/main/hosts)
Then create new Ansible playbook to use for your new Elk Vm curl [elk.yml](
Run ansible-playbook elk.yml
After the Elk container is installed double check elk-docker container is running by SSH into Elk VM ssh azureuser@[private IP address]
Run sudo docker ps
Since the Elk server runs on port 5601 you need to create an incoming rule for the security group that allows TCP traffic over the port 5601 from your IP address.
Check that you can load the ELK stack server at http://[your.VM.IP]:5601/app/kibana.
If everthing works correcty, you should see the home webpage of kibana.
