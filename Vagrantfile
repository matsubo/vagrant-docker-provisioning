VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # always use Vagrants insecure key
  config.ssh.insert_key = false

  # plugin conflict
  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  $shared_folders = [['./', '/docker']]
  $shared_folders.each_with_index do |(host_folder, guest_folder), index|
    config.vm.synced_folder host_folder.to_s, guest_folder.to_s, id: "core-share%02d" % index, nfs: true, mount_options: ['nolock,vers=3,udp']
  end


  config.vm.network :private_network, ip: '172.17.8.100'


  # redis, mysql Port Forwarding
  config.vm.network "forwarded_port", guest: 25,   host: 8025
  config.vm.network "forwarded_port", guest: 3306, host: 3306
  config.vm.network "forwarded_port", guest: 6379, host: 6379


  config.vm.box = "coreos-alpha"

  config.vm.provision "docker-build", type: "docker" do |d|
    d.build_image "/docker/mysql",     args: '-t mysql'
    d.build_image "/docker/redis",     args: '-t redis'
    d.build_image "/docker/postfix",   args: '-t postfix'
  end


  config.vm.provision "docker-run", type: "docker", run: "always" do |d|
    d.run "mysql", args: "-p 3306:3306 --name mysql -e DB_NAME=dpa_development -e DB_USER=docker -e DB_PASS=docker"
    d.run "redis", args: "-p 6379:6379 --name redis"
    d.run "postfix", args: "-p 25:25 --name postfix"
  end



end

