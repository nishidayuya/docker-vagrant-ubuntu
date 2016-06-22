# docker-vagrant-ubuntu

A Ubuntu Docker image for Vagrant Docker provider.

This image is based on [official Ubuntu image](https://hub.docker.com/_/ubuntu/) and includes minimum Vagrant box features.

# Supported tags and respective `Dockerfile` links

* [`12.04.5`, `12.04`, `precise`, `latest` *Dockerfile*](https://github.com/nishidayuya/docker-vagrant-ubuntu/blob/master/Dockerfile)

Issues and pull-requests are available on [GitHub repository](https://github.com/nishidayuya/docker-vagrant-ubuntu/).

# Usage

Write `Vagrantfile` as following:

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV["VAGRANT_DEFAULT_PROVIDER"] ||= "docker"
Vagrant.configure(2) do |config|
  config.vm.provider(:docker) do |d|
    d.image = "nishidayuya/docker-vagrant-ubuntu:precise"
    d.has_ssh = true
  end
end
```

Enjoy `vagrant up`, `vagrant ssh` and so on!

```
$ vagrant up
Bringing machine 'default' up with 'docker' provider...
==> default: Creating the container...
    default:   Name: try_default_1466597433
    default:  Image: nishidayuya/docker-vagrant-ubuntu:precise
    default: Volume: /home/yuya/try:/vagrant
    default:   Port: 127.0.0.1:2222:22
    default:
    default: Container created: e1c3e52c432c3645
==> default: Starting container...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 172.17.0.3:22
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
$ vagrant ssh
Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 3.16.0-4-amd64 x86_64)

 * Documentation:  https://help.ubuntu.com/
vagrant@e1c3e52c432c:~$ sudo apt-get update
...
```
