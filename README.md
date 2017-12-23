# elk-stack
Ansible repo to install ELK (elasticsearch, logstash, Kibana) stack

## Usage and Example Playbook

Install Java, Elasticsearch, Logstash and Kibana roles from Ansible Galaxy into your roles directory of ELK stack repo.


**Installing multiple roles from a file** 

Beginning with Ansible 1.8 it is possible to install multiple roles by including the roles in a requirements.yml file. The format of the file is YAML, and the file extension must be either .yml or .yaml.

Use the following command to install roles included in requirements.yml into roles/ directory of ELK stack repo:
```yml
$ ansible-galaxy install -r requirements.yml -p roles/
```
**OR install one by one**

```
$ ansible-galaxy install avinash6784.oracle-java
$ ansible-galaxy install avinash6784.elasticsearch
$ ansible-galaxy install avinash6784.logstash
$ ansible-galaxy install avinash6784.kibana
```
**OR download manually**

```
$ git clone https://github.com/avinash6784/ansible-oracle-java.git
$ git clone https://github.com/avinash6784/ansible-role-elasticsearch.git
$ git clone https://github.com/avinash6784/ansible-role-logstash.git
$ git clone https://github.com/avinash6784/ansible-role-kibana.git
```
The code should reside in the roles directory of elk stack ( See ansible documentation for more information on roles ).


## Run the playbook

First create a playbook including the git role, naming it elk-stack-install.yml.
```yml
- name: Install ELK Stack
  hosts: localhost
  become: true
  roles:
    - { role: ansible-role-elasticsearch }
    - { role: ansible-role-logstash }
    - { role: ansible-role-kibana }

$ ansible-playbook -i hosts elk-stack-install.yml