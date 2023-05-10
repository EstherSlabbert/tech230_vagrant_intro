# language: Ruby
# OS templates = boxes, OS usually Linux
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64" # configures OS for VM, this one is older, but stable
  config.vm.network "private_network", ip:"192.168.10.100"

end

# STEPS
# Open VirtualBox
# Set folder destination for VM in terminal
# Create VM file instructions with vagrant. In terminal: vagrant init
# open Vagrantfile and remove comments and set OS
# Create VM and activate. In terminal: vagrant up
# Uses ssh key to determine who is using it and enter machine. In terminal: vagrant ssh
# Now inside VM shown by vagrant@ubuntu-xenial:~$ username in terminal.

# Deploy basic html website (requires server (patchi or nginx))

# sudo (super user do, give me admin rights for this specific command)
# apt = package manager (apt-get = instructions for package manager)
# update = gets updates, but doesn't put them into effect
# upgrade = puts updates into effect (all latest versions)
# -y = flag for permission to say 'yes', so it doesn't ask later ~ automation
# install = installs something

# In terminal: sudo apt-get update
# done

# In terminal: sudo apt-get upgrade -y
# done

# get web server
# In terminal: sudo apt-get install nginx -y
# Starts program. In terminal: sudo systemctl start nginx
# Checks status. In terminal: sudo systemctl status nginx
# Ctrl + C kicks out or type in terminal: q
# vagrant ssh joins
# Set IP address (any number under 255). In vagrant file under config.vm.box line: config.vm.network "private_network", ip:"192.168.10.100"
# Return/logout to restart VM. In terminal: exit
# Shutsdown and restarts VM with added instructions/features in vagrant file. In terminal: vagrant reload

# checks nginx. In terminal: sudo systemctl status nginx
# can go to 192.168.10.100 in web browser and see deployed webserver
