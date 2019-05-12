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
- Copy group_vars/all.example to group_vars/all and edit what you need
- Change hosts file with valid hosts of ~./ssh/config
- Change main.yml hosts to match desired host, for example localhost, or vagrant
- Change main.yml the remote_user that will execute the script.
    If some tasks needs to be run as root, they are flagged with become: yes (spoiler: apt)
- Execute playbook:
```
ansible-playbook main.yml -i . -v -v
```
Explanation:
-i refers to the hosts inventory file, if not specified it fill find hosts in /etc/ansible/hosts