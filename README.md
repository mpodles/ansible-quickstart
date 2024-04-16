The install procedure on Ubuntu 22:

    sudo apt update 
    sudo apt install software-properties-common 
    sudo add-apt-repository --yes --update ppa:ansible/ansible 
    sudo apt install ansible

After installing, the ansible and ansible-playbook commands become available:

**ansible-playbook -i <inventory name> -kK [--list-hosts, --list-tasks] [-t, --limit <hosts_group>] <playbook name>**
- i - inventory file (eg. example_hosts)
- k - ask user for ssh password
- K - ask user for escalation password
- --list-hosts and/or --list-tasks - the playbook won't run but will show what hosts and tasks will be run

Inventory **example_hosts** file specifies hosts that can be "played" on. For example, with an entry: 

    some_server1 
ansible will try connecting with SSH using DNS hostname(some_server1) unless You specify IP with ansible_host variable:

    some_server1 ansible_host=XX.XX.XX.XX

Variables in plays and tasks are taken from *group_vars* and *host_vars* but can also be supplied from command line when running ansible command. Their precedence can be found at:
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable
