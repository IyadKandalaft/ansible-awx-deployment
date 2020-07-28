# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  config.vm.synced_folder ".", "/vagrant", disabled: true


  config.vm.provider "virtualbox" do |vb| 
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
    vb.cpus = "2"
  end
  
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 8443

  config.vm.provision "ansible" do |ansible|
    ansible.become = true
    #ansible.galaxy_role_file = "requirements.yml"
    ansible.playbook = "site.yml"
    ansible.galaxy_command = "ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path}"
    ansible.compatibility_mode = "2.0"
  end
end
