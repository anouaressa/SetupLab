Vagrant.configure("2") do |config|
    servers=[
        {
          :hostname => "control",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.50",
          :ssh_port => '2201'
        },
        {
          :hostname => "web01",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.51",
          :ssh_port => '2202'
        },
        {
          :hostname => "web02",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.52",
          :ssh_port => '2203'
        },
        {
          :hostname => "web03",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.53",
          :ssh_port => '2204'
        },
        {
          :hostname => "db",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.54",
          :ssh_port => '2205'
        },
        {
          :hostname => "LoadBalancer",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.55",
          :ssh_port => '2206'
        }
      ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", 300]
                vb.customize ["modifyvm", :id, "--cpus", 1]
            end
        end
    end
end