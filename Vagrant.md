# What it is

in a nutshell vagrant is a tool to load installed Linux OS on one of virtualization tool like `Oracle VM virtual box`, `hyper visor`.



# Box

everything in vagrant is based on box.

based on my understanding, box is an immutable image that make it possible to create our VM based on it, and extend it (for example install a specific package in VM before run it).

you can search your desire box in repository :

[Vagrant]: https://app.vagrantup.com/boxes/search	"Vagrant Box Repository"



to add a box in our local machine we can add it by using its name; for example if we want to add a box named `hashicorp/bionic64`, we can execute following command in our local machine:

```powershell
vagrant add box hashicorp/bionic64
```

 

above command will download box `hashicorp/bionic64` from vagrant box repository and store it in `$ENV:UserProfile\.vagrant.d\boxes` (this path is for Windows OS) path of local machine. 



### Use a Box

to use a box, write the following command in a file named `Vagrantfile`:

```powershell
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
end
```



by executing above command, if box `hashicorp/bionic64` exists in your local machine, vagrant will use it and then run a VM based on it, or download it from vagrant box repository and then run a VM based on it.



to execute command on a `Vagrantfile`, navigate to the directory where the file resides and execute the following command:

```powershell
vagrant up
```



# list boxes

to see the list of downloaded boxes in local machine, execute the following command:

```powershell
vagrant box list
```



# remove a box

to remove the physical files related to the image of a box from your local machine use the `remove` command; say we want to remove box `hashicorp/bionic64`, execute the following command:

```powershell
vagrant box remove hashicorp/bionic64
```

  

# sync VM and guest files

we have a directory that our `Vagrantfile` exists inside it and we created our `VM` by running this `vagrantfile`; say this directory name is `my-gust-machine-vagrant-dir`. all contents that resides in the directory `my-gust-machine-vagrant-dir`, are shared between `VM` running and  gust machine.

inside root directory of the running `VM` there is a directory named `vagrant`, which is synced with directory `my-gust-machine-vagrant-dir`. it means every file inside `my-gust-machine-vagrant-dir` do exists in `vagrant` directory of the `VM` machine.  
