Hadoop MapReduce and HDFS configuration
=========

This role will configure MapReduce and HDFS cluster and connect them, and configure a cclient to perform further operations.

Requirements
------------

Have atleast 5 instances ready to be configured as namenode, datanode, jobtracker, tasktracker and a client. We can use as many datanodes and tasktrackers required.

The machine where this role will be executed needs to have 
hadoop and jdk rpm in /root.

Run this command

```
chmod 400 <path-of-key-file>
```

Role Variables
--------------

namenodeip -> public ip of namenode
jobtrackerip -> public ip of jobtracker
folder_namenode -> directory inside namenode
port_namenode -> port where namenode is running
folder_datanode -> directory inside datanode
port_jobtracker -> port where jobtracker is running
software_drt -> directory inside all this nodes, where jdk and hadoop rpm will be stored

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

create the setup.yml file like-

```
- hosts: all
  roles:
  - role: "<path-of-role-folder>"

```

create the ansible.cfg file like-

```
[defaults]
host_key_checking = False
roles = <path-of-role-folder>
inventory = <path-of-inventory-file>
ask_pass = False
remote_user = ec2-user
private_key_file = <path-of-key-file>
[privilege_escalation]
become = True
become_method = sudo
become_user = root
become_ask_pass = False
```

set the roles path with the following -

```
ansible-playbook <path-of-setup.yml> --roles-path <path-of-role-folder>
```

License
-------

Apache-2.0

Author Information
------------------

Yash Indane

Email: yashindane46@gmail.com
