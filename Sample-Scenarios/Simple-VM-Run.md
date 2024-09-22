# Subject

we want to run a Linux OS based on box `hashicorp/bionic64` with a user with username `vagrant` in `Oracle VM VirtualBox`; then connect it by `ssh` with username `vagrant`.



# create `Vagrantfile`

create a directory named `vagrant-test` and navigate to it and run the following command:

```powershell
vagrant init
```



this will create a file named `Vagrantfile` in directory `vagrant-test`; open it and replace line containing command `config.vm.box = "base"` with `config.vm.box = "hashicorp/bionic64"`, and remove all comments. final content of the `Vagrantfile` should be as follow:

```powershell
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
end
```



**HINT:** you can also execute the command `vagrant init hashicorp/bionic64`, instead of `vagrant init` to have the final `Vagrantfile` without need to replace command `config.vm.box = "base"`.



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

