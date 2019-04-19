# Example 6
#
# Pulling out all the stops with cluster of seven Vagrant boxes.
#
domain   = 'chandler.com'

nodes = [
  { :hostname => 'master1',   :ip => '192.168.0.42', :box => 'generic/rhel7' },
  { :hostname => 'master2',      :ip => '192.168.0.43', :box => 'generic/rhel7' },
  { :hostname => 'master3',    :ip => '192.168.0.44', :box => 'generic/rhel7' },
  { :hostname => 'node1',    :ip => '192.168.0.45', :box => 'generic/rhel7' },
  { :hostname => 'node2', :ip => '192.168.0.46', :box => 'generic/rhel7' },
  { :hostname => 'node3', :ip => '192.168.0.47', :box => 'generic/rhel7' },
  { :hostname => 'etcd1',   :ip => '192.168.0.48', :box => 'generic/rhel7' },
  { :hostname => 'etcd2',   :ip => '192.168.0.49', :box => 'generic/rhel7' },
  { :hostname => 'etcd3',   :ip => '192.168.0.50', :box => 'generic/rhel7' },
  { :hostname => 'lb1',   :ip => '192.168.0.51', :box => 'generic/rhel7' },
  { :hostname => 'lb2',   :ip => '192.168.0.52', :box => 'generic/rhel7' },
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = node[:box]
      nodeconfig.vm.hostname = node[:hostname] + ".box"
      nodeconfig.vm.network :private_network, ip: node[:ip]

      memory = node[:ram] ? node[:ram] : 256;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--cpuexecutioncap", "50",
          "--memory", memory.to_s,
        ]
      end
    end
  end

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.manifest_file = "site.pp"
    puppet.module_path = "puppet/modules"
  end
end

