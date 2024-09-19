![Lint](https://github.com/tbauriedel/vagrant-icinga-dev/actions/workflows/linting.yml/badge.svg)

# vagrant-icinga-dev

Vagrantfile with ansible provisioner.  
Installs and configures the Icinga stack inside of the box.

Image: `bento/rockylinux-8`  
Hostname: `icinga-dev`  
Provider: `VirtualBox`  

The following ports will be forwarded into the Vagrant box:
* 80 (guest) => 80 (host)
* 443 (guest) => 443 (host) // Webserver with TLS not configured via default
* 5665 (guest) => 5665 (host)
* 8086 (guest) => 8086 (host)

## Credentials

Default credentials if not customized (Format: `user` - `password`):
* Icinga Web 2 admin => `icinga` - `icinga`
* Icinga 2 API user => `poweruser` - `poweruser`
* IcingaDB-redis password => `redis-pass`
* Mysql `*.*` user => `poweruser` - `poweruser`
* Mysql root user: `root` - `root0815!`
* InfluxDB admin user: `admin` - `admin12345!`

## Components

The most common used components are pre-installed and configured.
* MySQL (Ansible role `geerlingguy.mysql`)
* Icinga (Ansible collection `icinga.icinga`)
  * Icinga 2
  * Icingadb
  * Icingadb Redis
  * Icinga Web 2
  * Icinga Director
* Graphite (Ansible collection `tbauriedel.gographite`)
  * go-carbon
  * carbonapi
* InfluxDB (Ansible collection `tbauriedel.influxdb2`)
  * InfluxDB v2

## Requirements

**Vagrant**
If you dont have it already check the official [installation guide](https://developer.hashicorp.com/vagrant/docs/installation).

**Ansible**
If you dont have it already check the official [installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

## Usage
Clone the repository: `git clone https://github.com/tbauriedel/vagrant-icinga-dev`

Move into repository: `cd vagrant-icinga-dev`

Install all needed ansible requirements: `ansible-galaxy install -r requirements.yml`

Add Icinga Subscription credentials [here](ansible/vars/icinga2_repo.yml).  
(If you dont have a subscription, just change the box to a debian based one)

Start the Vagrant box: `vagrant up`

---

To sync additional modules or similar into the box, you can use the example inside of the [Vagrantfile](Vagrantfile) (Currently commented out).
