Vagrant.configure("2") do |config|
  # Используем Ansible для провижининга
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "prov.yml"
    ansible.compatibility_mode = "2.0"
  end

  config.vm.define "DynamicWeb" do |vmconfig|
    # Ubuntu 22.04
    vmconfig.vm.box = "ubuntu/jammy64"
    vmconfig.vm.hostname = "DynamicWeb"

    # Проброс портов
    vmconfig.vm.network "forwarded_port", guest: 8083, host: 8083
    vmconfig.vm.network "forwarded_port", guest: 8081, host: 8081
    vmconfig.vm.network "forwarded_port", guest: 8082, host: 8082

    vmconfig.vm.provider "virtualbox" do |vbx|
      vbx.memory = "2048"
      vbx.cpus = "2"
      vbx.customize ["modifyvm", :id, "--audio", "none"]
    end
  end
end
