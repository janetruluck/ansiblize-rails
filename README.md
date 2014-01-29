#ansible-rails

Ansible playbooks for provisioning Ubunutu servers for rails applications. This is build with capistrano in mind, it sets up sudoers file for sudo-less management required by Capistrano 3.

##Current Playbooks:
* common - common tasks for ubuntu
  * update packages (via apt-get)
  * monit
  * iptables
  * fail2ban
  * basic ssh configuration
* appservers - provisions application servers
  * Unicorn
* webservers - provisions web servers
  * Nginx
* dbservers - provisions database server
  * Postgresql
* bgservers - provisions background job servers
  * Resque
* redisservers - provisions redis servers
  * Redis
* pubsubservers - provisions PubSub servers
  * Faye


## Setup

##### 1. Create the deploy user (this must be done on every host)

1. ssh into the server via root account
2. Add the deploy user `adduser deploy`
3. Add user to the sudo group `adduser deploy sudo` (optional)
4. Exit the server `exit`

##### 2. Ansibilize the hosts

Ansible is used to provision and setup the hosts for the application. 

```ruby
me@localhost: ansible-playbook -i staging ansibilize.yml -c paramiko --ask-sudo-pass
```