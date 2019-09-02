## 📝 Prerequisites
- Install Ansible:
```
apt install software-properties-common
add-apt-repository ppa:ansible/ansible
apt update
apt install ansible
```
- If need to execute in remote node: Hosts configured
By default in /etc/ansible/hosts, else when using ansible-playbook can use -i option and point to the hosts inventory.
A host inventory is just a file with headers: "[hosts_group]" and nodenames like "vagrant", this nodenames are defined in
~/.ssh/config with ssh config parameters.

## 💿 Usage
- Rename needed variables in all.yml
- If you are going to configure just one host, rename all.yml group_vars with host name
- Change hosts file with valid hosts of ~./ssh/config
- Change main.yml hosts to match desired host, for example localhost, or vagrant
- Change main.yml the remote_user that will execute the script.
    If some tasks needs to be run as root, they are flagged with become: yes (spoiler: apt)
- Execute playbook:
```
ansible-playbook main.yml -i . -v
```
Explanation:
-i refers to the hosts inventory file, if not specified it fill find hosts in /etc/ansible/hosts
You can algo use --limit localhost (or any other host)
And to see which hosts are catched by ansible you can add --list-hosts flag, that will only show hosts, not run the playbook.
