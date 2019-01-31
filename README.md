# minbootcamp
> Runbook to get Minh up-to-speed with some DevOps tools 

## Overview
1. Spin up a box (VM)
2. Clone some repositories we need inside the box
3. Install tools we need 
4. Dockerize our app
5. Expose our app to the outside world
6. Forward ports to laptop's browser (hosting the VM)
7. Edit our app and create a PR to this repository

### Setup Vagrant
Create a project dir in your desired location
```
$ mkdir minbootcamp
```

Download my image with chef pre-installed
```
$ vagrant box add edmamerto/bento-ubuntu-16.04-chef 
```
Create a vagrant file with my image configured in it
```
$ vagrant init edmamerto/bento-ubuntu-16.04-chef 
```
Check if your file was created
```
$ ls
```
Bring up your box 
```
$ vagrant up
```
Login to your box
```
$ vagrant ssh
```
### Download Repos
>Git should be pre-installed in your box

Make sure you're logged-in to your box. Below should return `vagrant`
```bash
$ echo $USER
```

Clone the app 
```
$ git clone https://github.com/edmamerto/handyflasky
```
Check if clone is successful
```
$ ls
```
Clone my chef cookbook which has docker installation recipe. This just makes it easier to install docker, and to get you introduced to chef.
```
$ git clone https://github.com/edmamerto/souschef
```
Expected output  when you run `ls` again
```
handyflasky
souschef
```
### Install Docker
Check if chef is installed
```
$ chef
```
Navigate to the chef projdir
```
$ cd souschef
```
Install docker through chef. For now just know that chef can automate what we would have manually done to install Docker like `sudo apt-get install <docker_stuff>`
```
$ sudo chef-client --local-mode --runlist "recipe[docker]"
```
Check if install was successful
```
$ docker
```
By default the docker daemon always runs as the root user. This just means you have to prepend `sudo` all the time. This can be annoying so let's add your user which is `vagrant` to the docker group. 
```
$ sudo usermod -aG docker $USER
```
For this to take effect. Logout and login of your box
```
$ exit
$ vagrant ssh
```
Check if you're now able to run without `sudo`. You should not get a `permission denied` when you run command below
```
$ docker ps
```
