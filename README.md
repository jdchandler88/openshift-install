# openshift-install
Vagrant creation of machines and ansible installation of openshift on the machines

## information
Information for installing OpenShift is obtained from https://docs.openshift.com/container-platform/3.9/.

## system architecture
The system will consist of 3 Kubernetes masters, 3 Kubernetes nodes, 3 etcd nodes, and 2 HAProxy machines. The 2 HAProxy machines exist for the purpose of reverse-proxy/load-balancer availability. If there were only one, then the load-balancer is a single point of failure. *Note that the HAProxy config is not recommended in production according to RedHat. They recommend an F5 or Cisco appliance* Requirements for each of the machine types are located here: https://docs.openshift.com/container-platform/3.9/install_config/install/prerequisites.html

## installation
### prerequisites
Use the prerequisite link above to size your host machine[s] appropiately. 
For example, the strategy for creating the OpenShift cluster is to create an Ubuntu 16.04 virtual machine with 350GB disk space, 4CPUs, and 16GB memory. This number comes from
* 3 master nodes (minimum of 40GB disk space each) = 120GB
* 3 nodes (minimum 30GB disk space each) = 90GB
* 3 etcd nodes (minimum 20GB disk space each) = 60GB 
* 2 HAProxy nodes (don't know the minimum, assuming 20GB) 40GB
* overhead for host machine ~20GB

This accounts for a total of 330GB. Adding additional 20GB for safety.



### procedure
* Install Git on host machine. 'sudo apt-get install git'
* Install Virtualbox on host machine. 'sudo apt-get install virtualbox'
* Install Vagrant on host machine. https://www.vagrantup.com/docs/installation/
* Install Vagrant plugin, vagrant-disksize. 'vagrant plugin install vagrant-disksize'
** Out of the box, Vagrant does not enable sizing of a disk. Vagrant boxes all come pre-sized. Note that this tends to lock Vagrantfiles into a Vagrant provider (e.g. Virtualbox)


Vagrant and Ansible must be installed on the Ubuntu host VM. Vagrant will be used to create the cluster machines and Ansible will be used to do pre-installation configuration. 

procedure found on RHEL openshift website
