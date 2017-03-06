#### Check IP configuration

`ifconfig -a`

make `eth0` IP address to be static
* [X] Using the MAC Id/Harware address, router can always assign the specific IP address always
* [X] Get the Gateway address from `route -n`
* [X] `Edit Connection` (Network Connections)
* [X] IPv4Settings-> Manual Key-in the details as below
* [X] Address: Allready assigned IP address found from `ifconfig -a`
* [X] Gateway: From `route -n`
* [X] Net Mask: from above command

#### Alternatively

* [X] The above settings can be done in a file `/etc/network/interfaces`
* [X] Values are for indication purpose


    auto eth0
    iface eth0 inet static
    address 10.0.0.100
    netmask 255.255.255.0
    gateway 10.0.0.1
    
#### Add 'git' user    
`sudo adduser git`

#### Install openssh-server    
`sudo apt-get install openssh-server`
*To access by key not by plain text password:*
Edit the file `/etc/ssh/sshd_config` and make sure you have `PasswordAuthentication no`


#### Bare git project

* [X] Create a directory where git code would reside, may be `/opt/git/hello-world.git/`
* [X] Give ownership to **git** `sudo chown -R git:git git`
* [X] `cd /opt/git/hello-world.git/`
* [X] `sudo git init --bare`

#### Add client keys


__Look at [client](./client.md) how know, how to generate Keys that can be shared with Server and 
acess can be made without a password, securely.__

    sudo mkdir /home/git/.ssh
    sudo chmod 700 .ssh
    sudo touch /home/git/.ssh/authorized_keys
    sudo chmod 600 /home/git/.ssh/authorized_keys
    sudo mv ~/client_id_rsa.pub /home/git/
    sudo cat  /home/git/client_id_rsa.pub >> /home/git/.ssh/authorized_keys 

#### Change git' shell 
Edit `/etc/shells` (valid login shells for different users) with `git-shell`  
'git-shell' value can be obtained from running `which git-shell`

Change the log-in shell for git user

`sudo chsh git <which git-shell>`
This make a client can not log into a server's shell

####  Limited git-log in shell for a client
     
    sudo cp /usr/share/doc/git/contrib/git-shell-commands /home/git/ -R
    sudo chown git:git /home/git/git-shell-commands/ -R
    sudo chmod +x /home/git/git-shell-commands/help 
    sudo chmod +x /home/git/git-shell-commands/list
    sudo su git
The above steps make it possbile for a client to log into server with username 'git' and gets 
a very limited capability shell (git shell)

