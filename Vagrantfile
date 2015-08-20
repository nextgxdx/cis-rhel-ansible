# vi: set ft=ruby :
#
# The purpose of this is to use the 'cis' role as an ansible
# provisioner for Vagrant.
#
#

$setup= <<-EOT
pip install python-keyczar
EOT

Vagrant.configure(2) do |config|
  config.ssh.username = 'ngd'
  config.vm.box = "nextgxdx/centos7master"
  config.vm.provision "shell", inline: $setup
  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = {
      cis_user: 'ngd',
      grub_conf: '/etc/grub2.cfg'
     }
    ansible.playbook = "playbook.yml"
  end
end
