# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV["VAGRANT_DEFAULT_PROVIDER"] ||= "docker"
Vagrant.configure(2) do |config|
  config.vm.provider(:docker) do |d|
    d.image = "nishidayuya/docker-vagrant-ubuntu:trusty"
    d.has_ssh = true
  end
end
