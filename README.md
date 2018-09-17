# kitchen-mysql64
Kitchen-vagrant test for Vagrant box

## Prerequisites: 
* [VirtualBox](https://www.virtualbox.org/manual/ch02.html)
* [Vagrant](https://www.vagrantup.com/downloads.html)

**This repository contains instructions how to perform
kitchen-vagrant test on the box built from [this](https://github.com/firedot/packer-mysql64.git) repository **

1. Follow the instructions from the repository quoted above. 
2. Once the process is completed, run the following command: 
````
vagrant box add --name mysql64 mysql64.box
````
** This will make the box created with packer available to vagrant**
   * 2.1 Another way to obtain the box is by executing the following command: 
   
     ````
      vagrant box add firedot/mysql64
     ````
      The previous line will download the already built box from the VagrantCloud. 
3. Install kitchen by installing the [ChefDK](https://downloads.chef.io/chefdk)
4. Clone this repository: 
  ````
  git clone https://github.com/firedot/kitchen-mysql64.git 
  ````
## How to test: 
1. Go into the cloned repo dir
2. Type: 
  ````
  kitchen converge
  
  #A converge will leave the machine running and kitchen automatically uploads changes each converge so that one can iterate rapidly on configuration code.
  ````
3. Type: 
  ````
  kitchen verify
  
  #Does verifications based on the file located in ./test/integration/default/ 
  #In this case, checks for particular packages described in ./test/integration/default/check_pkg.rb
  ````
4. To destroy machine that's being tested, run: 
  ````
  kitchen destroy
  ````
  
## You may do all of the above in automated manner

  ````
  kitchen test
  ````





