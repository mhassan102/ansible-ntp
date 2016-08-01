
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "site" do |site|

    site.vm.provider :virtualbox do |provider, override|
      override.vm.box = "ubuntu/trusty64"
      override.vm.network :private_network, ip: "192.168.33.10"
    end

    site.vm.provider :digital_ocean do |provider, override|
      override.vm.box = "digital_ocean"
      override.ssh.private_key_path = 'redacted'
      provider.token = "redacted"
      provider.image = "ubuntu-14-04-x64"
      provider.region = "nyc2"
      provider.size = "1gb"
    end

    site.vm.provision "ansible" do |ansible| 
      ansible.playbook = "site.yml"
      ansible.verbose = 'vvv'
    end 

  end
end
