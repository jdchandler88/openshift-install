# openshift-install
Vagrant creation of machines and ansible installation of openshift on the machines

## information
Information for installing OpenShift is obtained from https://docs.openshift.com/container-platform/3.9/.

## system architecture
The system will consist of 3 Kubernetes masters, 3 Kubernetes nodes, 3 etcd nodes, and 2 HAProxy machines. The 2 HAProxy machines exist for the purpose of reverse-proxy/load-balancer availability. If there were only one, then the load-balancer is a single point of failure. *Note that the HAProxy config is not recommended in production according to RedHat. They recommend an F5 or Cisco appliance* Requirements for each of the machine types are located here: https://docs.openshift.com/container-platform/3.9/install_config/install/prerequisites.html

## installation
### prerequisites
vagrant install
rhel7
### procedure
procedure found on RHEL openshift website
