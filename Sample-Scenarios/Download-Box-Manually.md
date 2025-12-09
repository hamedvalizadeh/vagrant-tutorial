# Subject

we want to download image box for OS `Ubuntu 22.04` manually and add it to vagrant on Windows 11 as HOST OS, and based on that box with a user with username `vagrant` in `Oracle VM VirtualBox`; then connect it by `ssh` with username `vagrant`.



# Download Box

navigate to the web page `https://portal.cloud.hashicorp.com/vagrant/discover/bento/ubuntu-22.04` and `amd64` version of `virtualbox` download file. at the time of this tutorial the downloaded file name was `9bb215b1-b2c0-11f0-8804-5adb906f1608`, we renamed it to `ubuntu-22.04-virtualbox.box`.



# Add Box

after downloading the image box of the OS, execute the following command to add the file to vagrant box:

```
vagrant box add bento/ubuntu-22.04 ubuntu-22.04-virtualbox.box
```



to check that the box is added to the vagrant, execute following command:

```
vagrant box list
```



in the result of the above command you should se following:

```
bento/ubuntu-22.04 (virtualbox, 0, (amd64))
```



# create `Vagrantfile`

create a directory named `vagrant-test` and navigate to it and run the following command:

```powershell
vagrant init
```



this will create a file named `Vagrantfile` in directory `vagrant-test`; open it and replace its content with following lines.. final content of the `Vagrantfile` should be as follow:

```powershell
IMAGE_ubuntu_2204   = "bento/ubuntu-22.04"
IMAGE_Debian_12     = "bento/debian-12"

Vagrant.configure("2") do |config|
  config.vm.box = IMAGE_Debian_12
  config.vm.hostname = "test"
  config.vm.provider "virtualbox" do |my_vm|
    my_vm.name = "my_vm"
    my_vm.memory = 1024
    my_vm.cpus = 1
  end
  #config.vm.provision :shell, path: "bootstrap.sh"
end
```



# run the VM

to do so, navigate to the directory `vagrant-test` and execute the following command:

```powershell
vagrant up
```

  

after completing the execution of the above command, you will have a new VM in your `oracle VM VirtualBox` list that is in running mode.



# connect to VM

to do so, navigate to the directory `vagrant-test` and execute the following command:

```
vagrant ssh
```

  

now you are in your VM Linux OS with the username `Vagrant`.



# destroy VM

to do so, navigate to the directory `vagrant-test` and execute the following command:

```powershell
vagrant destroy
```

