# -*- mode: ruby -*-

# vi: set ft=ruby :

boxes = [
    {
        :name => "server1",
        :eth1 => "192.168.205.10",
        :mem => "512",
        :cpu => "1"
    },
    {
        :name => "server2",
        :eth1 => "192.168.205.11",
        :mem => "512",
        :cpu => "1"
    },
    {
        :name => "server3",
        :eth1 => "192.168.205.12",
        :mem => "512",
        :cpu => "1"
    }
]

Vagrant.configure(2) do |config|

  config.vm.box = "debian/jessie64"

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]

      config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", opts[:mem]]
        v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
        v.customize ["modifyvm", :id, "--name", opts[:name]]
      end

      config.vm.network :private_network, ip: opts[:eth1]
    end
  end
end