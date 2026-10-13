# Control Node

A node in which you run Ansible CLI tools (ansible | ansible-playbook and others). 

Any computer that meets the software requirements for ansible can be used as a control node.

Ansible can be ran in containers know as Execution Environments, an EE image contains the following packages as standard

ansible-core
ansible-runner
Python
Ansible content dependencies

Execution Environments _can_ come with packages in addition to what's considered standard. Usually this involves other Ansible collections and their dependencies.

There *can* be multiple control nodes, Ansible itself however does not coordinate across them.

# Managed Nodes

Also referred as hosts, these are target devices that you aim to manage with Ansible.

Ansible itself is not usually installed on managed nodes, however an Ansible collection called *ansible_pull* can be installed on managed nodes that pull playbooks from a VCS (Version Control System i.e. Git) to executes them.