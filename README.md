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


