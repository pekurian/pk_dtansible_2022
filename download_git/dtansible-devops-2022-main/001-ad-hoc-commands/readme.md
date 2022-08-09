```
# restart without module
ansible all -a "sudo /sbin/reboot"

# restart with command and shell module
ansible all -m command -a "/sbin/reboot" -b
ansible all -m shell -a "/sbin/reboot" -b

# restart using reboot module
ansible all -m reboot -b

# get hostname
ansible all -m setup -a "filter=ansible_nodename"
ansible all -m shell -a "hostname"

# change hostname using module (change is visible after creating a new session)
ansible all -m hostname -a "name=matejmadeja" -b
ansible all -m hostname -a "name=node5" -b

# copy file from constrol node to all target nodes
ansible all -m copy -a "src=/tmp/test.txt dest=/tmp/haluz.txt"

# copy file in the target filesystem
ansible all -m copy -a "src=/tmp/test.txt dest=/tmp/haluz.txt remote_src=yes"

# create a new dir
ansible all -m file -a "path=/tmp/test state=directory"

# mv file
ansible all -m shell -a "mv /tmp/haluz.txt /tmp/test/haluz.txt"

# delete file/dir
ansible all -m file -a "path=/tmp/test state=absent"

# install package
ansible all -m apt -a "name=cmatrix state=present" -b
```