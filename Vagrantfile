VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.network "private_network", ip: "192.168.30.30"

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "start.yml"
    ansible.sudo = true
    ansible.host_key_checking = false
  end

  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "40"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
  end
end
