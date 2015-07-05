Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  config.vm.define "bang-dev1" do |node|
    node.vm.box = "ubuntu14"
    node.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
    node.vm.network :private_network, ip: "192.168.33.10"
    node.vm.network :forwarded_port, guest: 3000, host: 3000
    node.ssh.insert_key = false
  end
end
