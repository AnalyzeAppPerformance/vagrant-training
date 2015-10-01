Przydante linki:

# Vagrant
### Synchronizacja plików
1. Plugin dla windowsiarzy - NFS https://github.com/winnfsd/vagrant-winnfsd, pozwala ustawić typ synchronizacji "nfs", dzięki czemu działa to płynniej :)
2. Automatyczna zmiana właściciela plików np na ``www-data`` https://github.com/gael-ian/vagrant-bindfs i przykład wpisu do ``Vagrantfile``

```
config.bindfs.bind_folder "/var/www/your-website", "/var/www/your-website", user: 'www-data', group: 'www-data'
```

3. Poprawka dla brakującego ansible na windowsy:

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
Dokumentacj: https://docs.ansible.com/ansible/index.html
Best Practices: https://docs.ansible.com/ansible/playbooks_best_practices.html
Rejestr i szukajka gotowych ról https://galaxy.ansible.com/list#/roles?page=1&per_page=10&sort_order=owner__username,name
Przykład skryptu robiącego deploy aplikacji webowej w ansible: https://github.com/servergrove/ansible-symfony2
Przykłady ról ansiblowych: https://github.com/ansible/ansible-examples

# Extra

Jeśli masz pytania do pisz na @DevOps lub mszczur@pgs-soft.com