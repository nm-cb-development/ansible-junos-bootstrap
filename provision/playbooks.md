# Ansible playbooks

## playbook_0

[A test drive playbook reading out the version of the junos boxes](https://github.com/roelsieg/ansible-junos-bootstrap/blob/master/provision/playbook_0.yml)

## playbook_1

[A test drive playbook provisioning the junos boxes with lldp](https://github.com/roelsieg/ansible-junos-bootstrap/blob/master/provision/playbook_1.yml)
```
vagrant ssh ansible
sudo ansible-playbook ./provision/playbook_1.yml
```
## playbook_2

[A playbook provisioning the junos boxes with simple BGP](https://github.com/roelsieg/ansible-junos-bootstrap/blob/master/provision/playbook_2/playbook_2.yml)
```
vagrant ssh ansible
sudo ansible-playbook ./provision/playbook_2/playbook_2.yml
```