# 

1. Start libvirtd
   ```
   sudo systemctl start libvirtd
   ```

1. Install vagrant-libvirt plugin
   ```
   vagrant plugin install vagrant-libvirt
   ```

1. Boot up two machines, `server` and `user`:
   ```
   vagrant up
   ```
   It will take some time the first time you run this
   command, cause we need to download the vagrant box.


1. Use ```vagrant ssh server``` and ```vagrant ssh user``` to
   connect to your machines.

1. Provision
   ```
   ansible-playbook playbook.yml
   ```
   It may take some time, be patient!

1. Final step   
   ```
   ansible 192.168.33.11 -b -a "systemctl set-default graphical.target"
   ```
   ```
   vagrant reload user
   ```

---
- `user` machine has gui enabled (through spice), use a spice client
   to connect to it
   ```
   remote-viewer spice://127.0.0.1:5900
   ```

- How to shutdown your machines
   ```
   vagrant halt
   ```
