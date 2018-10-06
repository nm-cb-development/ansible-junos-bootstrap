#
# Juniper lab v0.1
#
# ge-0/0/0.0: management interface
# ge-0/0/1.0 - ge-0/0/7.0: user interfaces

#default_box = 'image_to_use'
default_box = "juniper/ffp-12.1X47-D15.4-packetmode"

# Bowtie / Mesh Topology
# +---------+e3          e3+---------+
# | spine01 |--------------| spine02 |
# +---------+              +---------+
#   |e1    \ e2          e1 /    e2|
#   |        \            /        |
#   |          \        /          |
#   |            \    /            |
#   |              \/              |
#   |             /  \             |
#   |           /      \           |
#   |         /          \         |
#   |e1     / e2        e1 \     e2|
# +---------+              +---------+
# | leaf03  |--------------| leaf04  |
# +---------+e3          e3+---------+

Vagrant.configure(2) do |config|
  config.vm.box = default_box
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 2
    vb.gui = false
  end
  
  config.vm.define 'ansible' do |ansible|
	ansible.vm.box = "ubuntu/trusty64"
	ansible.vm.provision 'shell', inline: <<-SHELL
      sleep 30
	  sudo /vagrant/install.sh
    SHELL
  end
end

