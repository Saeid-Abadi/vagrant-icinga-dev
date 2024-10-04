#LOCAL_MODULES_PATH_GITHUB = "/Users/tbauriedel/workspace/github/tbauriedel/"

Vagrant.configure("2") do |config|
  config.vm.hostname = "icinga-dev"
  config.vm.box = "bento/rockylinux-8"
  #config.vm.synced_folder "#{LOCAL_MODULES_PATH_GITHUB}icingaweb2-module-graphite", "/usr/share/icingaweb2/modules/graphite"
  config.vm.provider "virtualbox"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.verbose = "v"
  end
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.network "forwarded_port", guest: 443, host: 443
  config.vm.network "forwarded_port", guest: 5665, host: 5665
  config.vm.network "forwarded_port", guest: 8086, host: 8086
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 3306, host: 3306
  config.vm.network "forwarded_port", guest: 8888, host: 8888
end
