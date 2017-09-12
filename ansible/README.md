#### Ansible

##### Requirements

- Install ansible
- Add your public key into remote/local host authorized_keys file. (you can login the host without password after this operation.)
- Create file hosts in /etc/ansible/. Add the host which you want to run ansible into it. (Just like the file in this project)

##### Commands

- Run command for all host

```bash
ansible all -m ping
```
- Run command for a group host

```bash
ansible local -m ping # Run command on local group hosts
ansible remote -m ping # Run command on remote group hosts
```