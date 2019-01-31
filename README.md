# minbootcamp
> Runbook to get Minh up-to-speed with some DevOps tools 

### Overview
1. Spin up a box (VM)
2. Clone some repositories we need inside the box
3. Install tools we need 
4. Dockerize our app
5. Expose our app to the outside world
6. Access our app from our laptop's browser (hosting the VM)
7. Edit our app and create a PR to this repository

### Setup Vagrant
Create a project dir in your desired location
```
$ mkdir minbootcamp
```

Download my image with chef pre-installed
```
$ vagrant add edmamerto/bento-ubuntu-16.04-chef 
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
### Download 
