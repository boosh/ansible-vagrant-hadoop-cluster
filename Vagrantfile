# Use this file to bring up a single-node hadoop cluster that doesn't use HDFS
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpus", "1", "--memory", "1024"]
  end

  config.vm.define "hadoop_single_node" do |hadoop_single_node|
    hadoop_single_node.vm.network "private_network", ip: "192.168.50.4"
    hadoop_single_node.vm.hostname = "hadoopsinglenode"

    hadoop_single_node.vm.provision :ansible do |ansible|
      ansible.inventory_path = "hosts-singlenode.yml"
      ansible.verbose = "vv"
      ansible.sudo = true
      ansible.playbook = "site.yml"
      ansible.limit = 'hadoop_all'
    end
  end
end