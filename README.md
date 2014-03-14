# Deploying Hadoop Clusters using Ansible & Vagrant

This project uses vagrant and ansible to launch a hadoop cluster running on
Ubuntu guests. To use, install vagrant & ansible, then just run `vagrant up`.

  * NameNode web interface: http://192.168.50.4:50070/
  * JobTracker web interface: http://192.168.50.4:50030/

**Note**: Hadoop will use a lot of disk space for the slaves.

For more information, see https://github.com/ansible/ansible-examples/tree/master/hadoop
which contains the original playbook, and this post which contained the
Vagrantfile http://leonidmirsky.com/ansible/hadoop/devops/2013/11/19/creating-hadoop-test-environment-with-ansible-and-vagrant.html.

Both needed modifying to work.

This comes with absolutely no warranty, etc. Make sure to comply with relevant
licences.
