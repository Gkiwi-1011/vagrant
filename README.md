# vagrant

## Preconditon
- Install vagrant (using Homebrew etc).
- share directory is created on the current directory(vagrant).

## Directory Configuration
    centos7/
    ├── vagrant
    │   ├── Vagrantfile
    │   └── share
    └── CentOS-7-x86_64-Minimal-1611.box

## Execute Commands
1. `vagrant box add  centos7 ../CentOS-7-x86_64-Minimal-1611.box`
 - Output: ** Comfirm Command is `vagrant box list`. **

2. `vagrant up`
 - Output: ** Running centos7 on Virtual Box. **

3. `vagrant ssh`
 - Output: ** Login centos7 on Virtual Box. **

4. `vagrant halt`
 - Output: ** Stop centos7 on Virtual Box. **

## Purpose
 - Standardization of the development environment.
 - Shorten the set-up time to develop applications.
 - Set up network interface to connect with other VMs,
 - Set up sync folder to share files with host.(The Default sync folder is `Vagrantfile's directory`.)

## About Provisioning
 - Build system easily.
 - Have high reproducibility.
 - Have identity between a development environment and a production environment.

## About Network
 - Port foward supports TCP.(If you use UDP, add `protocol:"udp"`.)
 - Static IP is used for only connection from Host to the guest or from the guest to another guest.(If you use static IP, add `config.vm.network "hostonly", "aaa.bbb.ccc.ddd"`.)
 - Bridge(that can connect from another host to guest using guest's IP.) supports only DHCP.(If you exmamine guest's IP, login the guest OS.)
 - eth0 is used for NAT(that is used for SSH port forward from Host) on Virtualbox and eth1 and eth2 are used for Guest IP.

## About Box
 - Box file is just tar file (that can be extracted).

## Remaining task
 - After getting new mac pc, Build vagrant environment using EC2 on AWS.(refer to P.222 on Vagrant book.)

## Update Kernel version on guest to set up VM guest additions
 - Update Kernel.`sudo yum -y install kernel`
 - Upadte other ones related kernel.`sudo yum install -y kernel-devel kernel-headers     dkms gcc gcc-c++`
 - Update all ones.`sudo yum update`
 - Check default boot kernel version.`sudo  awk -F\' '$1=="menuentry " {print i++ " :     " $2}' /boot/grub2/grub.cfg`
 - Change default boot kernel version.`sudo grub2-set-default`
 - Check changed default boot kernel version.`sudo grub2-editenv list`
 - Update default boot kernel version on grub2.`sudo grub2-mkconfig -o /boot/grub2/gr    ub.cfg`
