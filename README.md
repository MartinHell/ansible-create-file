# ansible-create-file

 Simple role that only creates a file. Used in the awesome friday project found at https://github.com/MartinHell/awesome_friday

## Lab #2
* Find the IP for the web server you just created.

* Login to the Ansible server over ssh

* Escalate privileges

```bash
sudo -i
```

* Check that the ansible server can connect to the webserver

```bash
ssh ubuntu@<ip of webserver>
```

* Disconnect from the webserver by pressing ctrl+d

* Change to the ansible directory

```bash
cd /etc/ansible
```

* Edit the hosts file using your preferred text editor

```bash
vim hosts
```

* Add the following text to the hosts file

```
[web]
web01
```

* Create a host_vars file for web01

```bash
vim host_vars/web01
```

* Add connection information for web01

```
---
ansible_host: <ip of web01>
```

* Create a playbook that adds the ansible-create-file role on web01

```bash
vim playbook.yml
```

* Add the following to playbook.yml

```text
---
- hosts: web
  tasks:
    - include_role:
        name: ansible-create-file
```

* Run ansible against the webserver

```bash
ansible-playbook -i hosts playbook.yml
```
If everything goes according to plan you should see that two changes happened. A new directory was created and a new file was added to that directory.

* Verify by logging into the webserver and checking the directory

```
ssh ubuntu@<ip of webserver>

ls -lah /tmp/my_first_directory/
```
