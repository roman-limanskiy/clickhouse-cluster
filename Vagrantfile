Vagrant.configure("2") do |config|

  config.vm.provider :virtualbox do |v|
    v.memory = 512
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/user.yml"
  end

  config.vm.define "clickhouse-01" do |clickhouse|
    clickhouse.vm.box = "ubuntu/xenial64"
    clickhouse.vm.hostname = "clickhouse-01"
    clickhouse.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.21"
  end

  config.vm.define "clickhouse-02" do |clickhouse|
    clickhouse.vm.box = "ubuntu/xenial64"
    clickhouse.vm.hostname = "clickhouse-02"
    clickhouse.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.22"
  end

  config.vm.define "clickhouse-03" do |clickhouse|
    clickhouse.vm.box = "ubuntu/xenial64"
    clickhouse.vm.hostname = "clickhouse-03"
    clickhouse.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.23"
  end

  config.vm.define "clickhouse-04" do |clickhouse|
    clickhouse.vm.box = "ubuntu/xenial64"
    clickhouse.vm.hostname = "clickhouse-04"
    clickhouse.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.24"
  end

  config.vm.define "zookeeper-01" do |zookeeper|
    zookeeper.vm.box = "ubuntu/xenial64"
    zookeeper.vm.hostname = "zookeeper-01"
    zookeeper.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.31"
  end

  config.vm.define "zookeeper-02" do |zookeeper|
    zookeeper.vm.box = "ubuntu/xenial64"
    zookeeper.vm.hostname = "zookeeper-02"
    zookeeper.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.32"
  end

  config.vm.define "zookeeper-03" do |zookeeper|
    zookeeper.vm.box = "ubuntu/xenial64"
    zookeeper.vm.hostname = "zookeeper-03"
    zookeeper.vm.network :public_network,
                          bridge: "wlx00e04c0a3bbc",
                          ip: "192.168.0.33"
  end
end
