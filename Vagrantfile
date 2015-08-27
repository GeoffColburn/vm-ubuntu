VAGRANTFILE_API_VERSION = "2"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu1404-puppet"
    ubuntu.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"

    ubuntu.vm.host_name = "vagrant"

    ubuntu.vm.network "public_network", type: "dhcp"
    ubuntu.vm.network "private_network", ip: "10.11.12.13"

    ubuntu.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 3000, host: 3000, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 8000, host: 8000, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 8085, host: 8085, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 9013, host: 9013, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 27017, host: 27017, auto_correct: true
    ubuntu.vm.network "forwarded_port", guest: 15672, host: 15672, auto_correct: true

    ubuntu.vm.synced_folder "share", "/share", create: true, nfs: true
    
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "vagrant.yml"
        #ansible.verbose = "v"
    end

    ubuntu.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", "2048"]
        vb.customize ["modifyvm", :id, "--cpus", "2"]
    end

  end

end
