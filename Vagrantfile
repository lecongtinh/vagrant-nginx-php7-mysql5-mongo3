# -*- mode: ruby -*-
# vi: set ft=ruby :

# Following 3 parameters should be set to suit your dev environment
web_application_code_directory_relative_to_this_directory = "../{your_app_on_host_relative_to_this_dir}"    # e.g., "../code/my_app"
web_application_root_directory = "{your_app_on_guest}"                                                      # e.g., "/var/www/my_app"

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "192.168.33.33"
  config.vm.synced_folder web_application_code_directory_relative_to_this_directory, web_application_root_directory, type: "nfs"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  config.vm.provision :ansible do |ansible|
    ansible.extra_vars = { WEB_APPLICATION_ROOT_DIRECTORY: web_application_root_directory }
    ansible.playbook = "local.yml"
    ansible.verbose = "vvv"
  end
end
