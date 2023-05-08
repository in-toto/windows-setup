Vagrant.configure("2") do |config|
  config.vm.box = "jborean93/WindowsServer2022"
  config.vm.communicator = "winrm"

  config.winrm.transport = "negotiate"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "default.yml"
    ansible.inventory_path = "inventory"
  end
end
