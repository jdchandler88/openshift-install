domain   = 'chandler.com'

nodes = [
  { :hostname => 'master1', :ip => '192.168.0.42', :box => 'generic/rhel7', :ram => '16384', :disk => '40GB', :cpus => 4, :user => "vagrant" },
  { :hostname => 'master2', :ip => '192.168.0.43', :box => 'generic/rhel7', :ram => '16384', :disk => '40GB', :cpus => 4, :user => "vagrant" },
  { :hostname => 'master3', :ip => '192.168.0.44', :box => 'generic/rhel7', :ram => '16384', :disk => '40GB', :cpus => 4, :user => "vagrant" },
  { :hostname => 'node1', :ip => '192.168.0.45', :box => 'generic/rhel7', :ram => '8192', :disk => '30GB', :cpus => 1, :user => "vagrant" },
  { :hostname => 'node2', :ip => '192.168.0.46', :box => 'generic/rhel7', :ram => '8192', :disk => '30GB', :cpus => 1, :user => "vagrant" },
  { :hostname => 'node3', :ip => '192.168.0.47', :box => 'generic/rhel7', :ram => '8192', :disk => '30GB', :cpus => 1, :user => "vagrant" },
  { :hostname => 'etcd1', :ip => '192.168.0.48', :box => 'generic/rhel7', :ram => '8192', :disk => '20GB', :cpus => 2, :user => "vagrant" },
  { :hostname => 'etcd2', :ip => '192.168.0.49', :box => 'generic/rhel7', :ram => '8192', :disk => '20GB', :cpus => 2, :user => "vagrant" },
  { :hostname => 'etcd3', :ip => '192.168.0.50', :box => 'generic/rhel7', :ram => '8192', :disk => '20GB', :cpus => 2, :user => "vagrant" },
  { :hostname => 'lb1', :ip => '192.168.0.51', :box => 'generic/rhel7', :ram => '8192', :disk => '20GB', :cpus => 1, :user => "vagrant" },
  { :hostname => 'lb2', :ip => '192.168.0.52', :box => 'generic/rhel7', :ram => '8192', :disk => '20GB', :cpus => 1, :user => "vagrant" },
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = node[:box]
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: node[:ip]
      nodeconfig.disksize.size = node[:disk]

      memory = node[:ram] ? node[:ram] : 256;
      cpus = node[:cpus] ? node[:cpus] : 1;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [ "modifyvm", :id, "--cpuexecutioncap", "50", "--memory", memory.to_s, "--cpus", cpus.to_s]
      end
    end
  end

  
end

