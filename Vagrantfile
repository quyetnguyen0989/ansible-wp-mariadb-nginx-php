#sudo vagrant init ubuntu/xenial64; vagrant up --provider virtualbox
vm_name = ENV['VM_NAME'] || 'default'
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  
  config.vm.box_check_update = false
  config.vm.define vm_name
  config.vm.hostname = vm_name

   # Networking
  #config.vm.network "forwarded_port", guest: 9090, host: 9090
  #config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 1443
  config.vm.network "forwarded_port", guest: 80, host: 1080

  config.vm.provision "ansible" do |ansible|
    # ansible.verbose = "vvv"
    ansible.playbook = "vg_playbook.yml" 

    ansible.groups = {
      "wordpress" => ["wp-host"],
      "wordpress:vars" => {
      "wp_version" => "4.2.4",
      "wp_sha256sum" => "42ca594afc709cbef8528a6096f5a1efe96dcf3164e7ce321e87d57ae015cc82",
      "wp_db_name" => "wordpress",
      "wp_db_password" => "123456abvI",

      }

    }
    ansible.host_vars = {
      "wp-host" => {
        "server_hostname" => "www.quyet.local",
        "auto_up_disable" => false,
        "core_update_level" => true,
      }
    }
  end 

end
