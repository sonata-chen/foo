# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "server" do |server|
    server.vm.box = "generic/fedora35"

    server.vm.hostname = "server.local"
    server.vm.network "private_network",
      ip: "192.168.33.10", hostname: true

    server.vm.provider "libvirt" do |domain|
      domain.graphics_type = "none"
      domain.video_type = "vga"
    end
  end

  config.vm.define "user" do |user|
    user.vm.box = "generic/fedora35"
    user.vm.hostname = "user.local"

    user.vm.network "private_network",
      ip: "192.168.33.11", hostname: true

    user.vm.provider "libvirt" do |domain|
      domain.video_type = "vga"
      domain.graphics_port = "5900"
      domain.graphics_ip = "127.0.0.1"
      domain.graphics_type = "spice"
      domain.video_vram = "16384"
    end
  end
end
