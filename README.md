This repository contain quick reference Ansible playbooks.

#### Simple Ping on all hosts ( using -m option for module)
`[root@localhost ansible]# ansible all -m ping`

#### With -a(attribute) option and -s ( to elevate access to sudo)
`[root@localhost ansible]# ansible all -a "uname"`
`ansible all -s -a "uname"`

#### Copy a file from localhost to remote host
`[root@localhost ansible]# ansible hdp_mgmt_nodes -m copy -a "src=test.txt dest=/tmp/test.txt"`
`[root@localhost ansible]# ansible hdp_mgmt_nodes -a "cat /tmp/test.txt"`

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
