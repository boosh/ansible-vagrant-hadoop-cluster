# Deploying Hadoop Clusters using Ansible & Vagrant

This project uses vagrant and ansible to launch hadoop on Ubuntu, either as
a single node (without HDFS) or as a cluster. To use, install vagrant &
ansible, then just run `vagrant up`.

By default a single node will be built. To build a cluster, set
`build_cluster` to True in the file `group_vars/all` and rename
`Vagrantfile.cluster` to `Vagrantfile` before running `vagrant up`.

Once built, the web UIs are available at:

  * JobTracker web interface: http://192.168.50.4:50030/
  * NameNode web interface: http://192.168.50.4:50070/ (cluster mode only)

**Note**: Hadoop will use a lot of disk space for the slaves when building a
cluster.

For more information, see https://github.com/ansible/ansible-examples/tree/master/hadoop
which contains the original playbook, and this post which contained the
Vagrantfile http://leonidmirsky.com/ansible/hadoop/devops/2013/11/19/creating-hadoop-test-environment-with-ansible-and-vagrant.html.

**Note**: The original examples provided a HA build. Getting that to work on
Ubuntu is left as an exercise for the reader ;-)

Both needed modifying to work.

This comes with absolutely no warranty, etc. Make sure to comply with relevant
licences.
