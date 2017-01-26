require_relative './vagrant/key_authorization'

Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--cpus", "2"] 
  end

  authorize_key_for_root config, '~/.ssh/id_dsa.pub', '~/.ssh/id_rsa.pub'

  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  {
    'omero'   => '192.168.41.11',
    'omero53'   => '192.168.41.12',
  }.each do |short_name, ip|
    config.vm.define short_name do |host|
      host.vm.network 'private_network', ip: ip
      host.vm.hostname = "#{short_name}.lmu.dev"
      host.vm.synced_folder ".", "/home/vagrant/sync", disabled: true
    end
  end
end
