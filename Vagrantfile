VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpus", "1", "--memory", "512"]
  end

  config.vm.define "hadoop_master" do |hadoop_master|
    hadoop_master.vm.network "private_network", ip: "192.168.50.4"
    hadoop_master.vm.hostname = "hadoopmaster"
  end

  config.vm.define "hadoop_slave1" do |hadoop_slave1|
    hadoop_slave1.vm.network "private_network", ip: "192.168.50.5"
    hadoop_slave1.vm.hostname = "hadoopslave1"
  end

  config.vm.define "hadoop_slave2" do |hadoop_slave2|
    hadoop_slave2.vm.network "private_network", ip: "192.168.50.6"
    hadoop_slave2.vm.hostname = "hadoopslave2"

    hadoop_slave2.vm.provision :ansible do |ansible|
      ansible.inventory_path = "hosts.yml"
      ansible.verbose = "v"
      ansible.sudo = true
      ansible.playbook = "site.yml"
      ansible.limit = 'hadoop_all'
    end
  end
end