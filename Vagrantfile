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
  config.vm.define 'spine01' do |spine01|
	spine01.vm.host_name = "spine01"
    #spine01.vm.box = default_box
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01l03',
                       ip: '169.254.13.1'#, auto_config: false
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01l04',
                       ip: '169.254.14.1'#, auto_config: false
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01s02',
                       ip: '169.254.12.1'#, auto_config: false
	config.vbguest.auto_update = false
    #spine01.vm.provision 'shell', inline: <<-SHELL
    #  sleep 30
    #  FastCli -p 15 -c "configure
    #  hostname spine01
    #  interface Management1
    #    ip address 192.168.56.101/24 secondary"
    #SHELL
  end
   config.vm.define 'spine02' do |spine02|
    spine02.vm.host_name = "spine02"
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's02l03',
                       ip: '169.254.23.1'#, auto_config: false
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's02l04',
                       ip: '169.254.24.1'#, auto_config: false
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's01s02',
                       ip: '169.254.21.1'#, auto_config: false
	config.vbguest.auto_update = false
  end
  config.vm.define 'leaf03' do |leaf03|
    leaf03.vm.host_name = "leaf03"
    leaf03.vm.box = default_box
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 's01l03',
                       ip: '169.254.31.1'#, auto_config: false
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 's02l03',
                       ip: '169.254.32.1'#, auto_config: false
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 'l03l04',
                       ip: '169.254.34.1'#, auto_config: false
	config.vbguest.auto_update = false
  end

  config.vm.define 'leaf04' do |leaf04|
    leaf04.vm.host_name = "leaf04"
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 's01l04',
                       ip: '169.254.41.1'#, auto_config: false
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 's02l04',
                       ip: '169.254.42.1'#, auto_config: false
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 'l03l04',
                       ip: '169.254.43.1'#, auto_config: false
	config.vbguest.auto_update = false
  end
end

