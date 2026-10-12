# What is Ansible?

Ansible is an open-source automation tool that reduces complexity and runs everywhere. Anisble can be used to automate virtually any task. 

Some use cases for Ansible

Eliminate repitition and simplify workflow 
Manage and maintain system configurations
Continuously deploy complex software
Perform zero-downtime rolling updates

Ansible uses simple human readable scripts called playbook to automate tasks, you declare the desired state of a local or remote system in a playbook; Ansible ensures the system remains in that state.

As an automation technology Ansible is designed around the following principles

### Agent-less
Ansible requires no agent to be installed on the local or remote resource you are targetting, this lowers maintenence across IT infrastructure because you can avoid the issues found with mass application deployments or additional application updates.

### Simplicity
Automation playbooks use YAML sytax for code that reads like documentation. Ansible is also decentralised because it uses SSH with whatever existing OS credentials to access remote machines.

### Scalability and Flexability
Easily and quickly scale the systems you automate through a modular design that supports a large range of operating systems, cloud platforms and networking devices.

### Idempotence and Predictability
When the system is already in the state the playbook describes Ansible does not change anything, even if the playbook runs multiple times.