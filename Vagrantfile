Vagrant.configure('2') do |config|
  config.vm.box      = 'ubuntu/trusty64'
  config.vm.hostname = 'dialect-php'

  config.vm.network :forwarded_port, guest: 8080, host: 8080

  # config.vm.provision :shell, path: 'bootstrap.sh', keep_color: true

  config.vm.network :private_network, ip: '192.168.50.50'
  config.vm.provision 'ansible' do |ansible|
    ansible.verbose = 'vv'
    ansible.playbook = 'setup.yml'
    ansible.inventory_path = 'vagrant-inventory'
    ansible.host_key_checking = 'false'
    ansible.limit = 'all'
    ansible.tags = %w(firewall) # sites php
  end

  config.vm.provider 'virtualbox' do |v|
    v.memory = 4096
  end
end
