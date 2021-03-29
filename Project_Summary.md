PROJECT 1 SUMMARY


What is ELK STACK?
 
"ELK is the acronym for three open source projects: Elasticsearch, Logstash, and Kibana. Elasticsearch is a search and analytics engine. Logstash is a server-side data
processing pipeline that ingests data from multiple sources simultaneously, transforms it, and then sends it to a 'stash' like Elasticsearch. Kibana lets
users visualize data with charts and graphs in Elasticsearch." (https://www.elastic.co/what-is/elk-stack


Background
- This project serves as a continuation of a previous lesson on Cloud Security where Azure was used to
create a virtual network. Network security was provided by a network security group and a load balancer.
A jump box provisioner was used as a control point to tunnel to three webservers (VMs) located in the network.
The IT automation engine, Ansible, was used to run playbooks. These playbooks are created as YAML or .yml  
files which Ansible "runs" to install the DVWA container on each of the VMs.


Objective

The goal for this project was to conduct an automated deployment of ELK stack.
- This project involved:
  - An understanding of network architecture (network diagrams)
  - Virtual network and virtual machine deployment using Azure
  - Introduction to Kibana using Filebeat and Metricbeat
  - Introduction to GitHub fundamentals
  - Scripting using YAML (.yml) files and running them through Ansible


Network Diagram

- The network diagram depicts the architecture of the 2 virtual networks and their respective attached virtual machines.
Red Team network has 4 machines total consisting of the jump box and 3 webservers (web-1, web-2, web-3). A load balancer connects with 
the 3 webservers using HTTP port 80. The jump box is the only machine that connect with the user's computer and communicates using SSH with the host's  public ip
address. Internally, the jump box communicates through SSH with the 3 webservers using private ip addresses. As mentioned in the README file, the jump box adds
security to the network because it acts as the sole "checkpoint" to the other virtual machines. The entire network is located behind a network security group which allows
certain traffic from specific ip addresses to pass through and into the network.

- Similarly, the ELK network consists of the Elk1 server VM which sits behind its own network security group. Peering connections allow communication with the Red Team
network. The jump box can be use to connect with the Elk-1 server using SSH port 22. The ELK server was created with a docker and runs Kibana. The local machine connects
to Kibana using HTTP on port 5601. This is one of three published port used with ELK. Elasticsearch listens to external TCP traffic on port 9200 and "Logstash uses
port 5044 to listen for incoming beat connections."(https://www.elastic.co/guide/en/beats/filebeat/current/logstash-output.html)


 



