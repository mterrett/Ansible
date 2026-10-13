# Playbook Keywords

A *playbook* is a list of plays that define the order in which Ansible performs operations from top to bottom to achieve an overall goal.

A *play* is an ordered list of tasks that maps to managed nodes in an inventory.

A *task* is the definition of an action to be appied to the managed host. Tasks can be executed ad hocby using *ansible* or *ansible-console*.

A *module* is a unit of code or binary that Ansible runs on managed nodes. Ansible modules are grouped in collections with a *Fully Qaulified Collection Name* for each module. 

A *collection* is the collation of modules and plugins. The collection index can be found at https://docs.ansible.com/projects/ansible/latest/collections/index.html#list-of-collections

A *handler* is a special form of task that only executes when notified by a previous task which resulted in a changed state.

