# Automating Nginx deployment

## Steps

1. Check [nginx_deployment.md](https://github.com/EstherSlabbert/tech230_vagrant_intro/blob/main/nginx_deployment.md) for steps in setting your 'Vagrantfile' up if you do not already have an appropriate file from using `vagrant init`.
2. Create a .sh file called 'provision.sh'. Open it and write the following:
    ```shell
    #!/bin/bash
    
    sudo apt-get update
    
    sudo apt-get upgrade -y
    
    sudo apt-get install nginx -y
    
    sudo systemctl start nginx
    ```
    Save the file (preferably in the same directory as your 'Vagrantfile' to make the path easier to find).
3. Open the 'Vagrantfile'. Add the line `config.vm.provision "shell", path: "provision.sh"`. Save. (If not already done: Remove comments. Change "base" to the name of your desired Operating System. Add an IP. Save.) Your 'Vagrantfile' should have the following/similar in it:
~~~ruby
Vagrant.configure("2") do |config|

  # configures OS for VM (this one is older, but stable)
  config.vm.box = "ubuntu/xenial64"
  # sets private IP address
  config.vm.network "private_network", ip:"192.168.10.100"

  # provisions the VM to have Nginx
  config.vm.provision "shell", path: "provision.sh"

end
~~~
4. Navigate to the correct location/directory that has your 'Vagrantfile' in your terminal using `cd`  if necessary.
5. Create/Activate/Run the Virtual Machine that your 'Vagrantfile' specifies by entering `vagrant up` in terminal. (This will take a while as it is completing everything specified in your 'provision.ssh' file.)(Note: to enter your VM in terminal after it is setup type `vagrant ssh`).
6. You should be able go to the IP address (in this case: 192.168.10.100) on your web browser & it will show you your deployed web server.

## Alternative steps

1. Check [nginx_deployment.md](https://github.com/EstherSlabbert/tech230_vagrant_intro/blob/main/nginx_deployment.md) for steps in setting your 'Vagrantfile' up if you do not already have an appropriate file from using `vagrant init`.
2. Open the 'Vagrantfile'. Add the line `config.vm.provision "shell", path: "shell, inline: <<-SHELL"` followed by the relevant instructions shown in the code block below and `SHELL` again. Save. (If not already done: Remove comments. Change "base" to the name of your desired Operating System. Add an IP. Save.)

Your 'Vagrantfile' should have the following/similar in it:
~~~ruby
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64" # configures OS for VM
  config.vm.network "private_network", ip:"192.168.10.100" # sets IP
  # configures automation of Ngnix deployment
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get upgrade -y
    sudo apt-get install nginx -y
    sudo systemctl start nginx
SHELL

end
~~~
3. Navigate to the correct location/directory that has your 'Vagrantfile' in your terminal using `cd` if necessary.
4. Create/Activate/Run the Virtual Machine that your 'Vagrantfile' specifies by entering `vagrant up` in terminal. (This will take a while as it is completing everything specified in your 'provision.ssh' file.)(Note: to enter your VM in terminal after it is setup type `vagrant ssh`).
5. You should be able go to the IP address (in this case: 192.168.10.100) on your web browser & it will show you your deployed web server.
