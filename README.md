## AD-HOC Commands
#### Simple Ping on all hosts ( using -m option for module)
`[root@localhost ansible]# ansible all -m ping`

#### With -a(attribute) option and -s ( to elevate access to sudo)
`[root@localhost ansible]# ansible all -a "uname"`
`ansible all -s -a "uname"`

#### Copy a file from localhost to remote host
`[root@localhost ansible]# ansible hdp_mgmt_nodes -m copy -a "src=test.txt dest=/tmp/test.txt"`
`[root@localhost ansible]# ansible hdp_mgmt_nodes -a "cat /tmp/test.txt"`
`[root@localhost ansible]# ansible all -m command -a "uptime"`

#### Install a package
`[root@localhost ansible]# ansible hdp_data_nodes -m yum -a "name=elinks state=latest"`
state values
latest -> Check if latest exist
absent -> If package exist uninstall
present -> If package exist, dont install.

#### Adding a user with password
`[root@localhost ansible]# ansible local -m user -a "name=mohit password=mohit"`


#### Removing a user 
`[root@localhost ansible]# ansible local -m user -a "name=mohit state=absent"`

## Ansible Playbook
#### Executing playbooks/structure.yml playbook
`root@localhost ansible]# ansible-playbook playbooks/structure.yml`


## Gathering facts 
#### Ad-hoc gathering facts
`ansible localhost -m setup`
OR
`[root@localhost ansible]# ansible localhost -m setup -a 'filter=*ipv4*'`

#### Create a file/dir locally to hold all the facts
`[root@localhost ansible]# ansible localhost -m setup --tree facts`
`[root@localhost ansible]# ls -ld facts`
`drwxr-xr-x. 2 root root 4096 Dec 23 23:41 facts`

#### Parameter passing to ansible script
`[root@localhost ansible]# ansible-playbook playbooks/parameters.yml`

#### Passing parameters from commandline
`[root@localhost ansible]# ansible-playbook playbooks/commandline_parameters.yml --extra-vars "myhosts=localhost gather=yes pkg=telnet"`

#### Debuging stmts
[root@localhost ansible]# ansible-playbook playbooks/debug.yml

#### Notifications
`[root@localhost ansible]# ansible local -m yum -a "name=httpd state=absent”`
`[root@localhost ansible]# ansible-playbook playbooks/notify.yml`
`[root@localhost ansible]# ansible-playbook playbooks/notify.yml`
