# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Box settings
  config.vm.box = "phusion/ubuntu-14.04-amd64"

  config.vm.provision :shell, inline: "sudo apt-get -y install python-pip"

  config.vm.provision :shell, inline: "yes | sudo pip install cqlsh==4.1.1"

  config.vm.provision :shell, inline: "sudo sysctl -w vm.max_map_count=262144"
  config.vm.network :forwarded_port, guest: 9200, host: 9202
  config.vm.network :forwarded_port, guest: 9300, host: 9300

  config.vm.provision "docker", images: ["elasticsearch:5.2.1"], run: "always" do |d|
    d.run(
      "elasticsearch",
      args: "--name elasticsearch -d --privileged=true -p 9200:9200 -p 9300:9300 -v /vagrant/elasticsearch:/usr/share/elasticsearch/config -e ES_JAVA_OPTS='-Xms1g -Xmx1g'"
    )
  end
end
