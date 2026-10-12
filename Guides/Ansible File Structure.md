/etc/ansible/hosts -- Default inventory file

/etc/ansible/ansible.cfg -- Config file, used if present

~/.ansible.cfg -- User config file, overrides the default config if present

./ansible.cfg -- Local config file (in current working directory) assumed to be 'project specific' and overrides the rest if present.

As mentioned above, the ANSIBLE_CONFIG environment variable will override all others.