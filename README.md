# Vagrant Training

Before you start to do this curse you have to install a few tools. Please follow by steps:

1. Go to [Download Virtualbox](https://www.virtualbox.org/wiki/Linux_Downloads) page and choose proper version
2. Go to [Download Vagrant](https://www.vagrantup.com/downloads.html) page and choose proper version
3. Go to [Ansible](http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu) page and choose proper version
4. Run the following commands:
  ```bash
  sudo apt-get update
  sudo apt-get install nfs-kernel-server
  ```

### If you use computer with preinstalled Ubuntu then you should choose version for Ubuntu 15.10

## Files Synchronization

* Plugin for Windows users that allow to run NFS sync up https://github.com/winnfsd/vagrant-winnfsd
* Plugin to change files owner ``www-data`` https://github.com/gael-ian/vagrant-bindfs and an example config in ``Vagrantfile``

```
config.bindfs.bind_folder "/var/www/your-website", "/var/www/your-website", user: 'www-data', group: 'www-data'
```

## How to use [Anbile](http://ansible.com) with [Vagrant](http://vagrantup.com) on [Windows](https://www.microsoft.com/)

```
v.vm.provision "shell",
    inline: "
        sudo apt-get --yes install software-properties-common;
        sudo apt-get --yes install python-pip;
        sudo apt-add-repository --yes ppa:ansible/ansible;
        sudo apt-get --yes update ;
        sudo apt-get --yes install ansible"
v.vm.provision "shell",
    inline: "
        set -x;
        cp -R /var/www/" + app_config["project_name"] + "/vagrant ~/;
        chmod -x ~/vagrant/provisioning/hosts;
        cd ~/vagrant/provisioning;
        ansible-playbook -i hosts site.yml;
    "
```

# Ansible

* Ansible Docs: https://docs.ansible.com/ansible/index.html
* Best Practices: https://docs.ansible.com/ansible/playbooks_best_practices.html
* Ansible Roles Registry https://galaxy.ansible.com/list#/roles?page=1&per_page=10&sort_order=owner__username,name
* Deploy Symfony2 App: https://github.com/servergrove/ansible-symfony2
* Samples: https://github.com/ansible/ansible-examples

# FAQ

If you have any questions feel free to contact me. job [at] michalszczur.pl
