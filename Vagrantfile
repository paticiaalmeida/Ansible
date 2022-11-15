
vms = {
    'Workpress' => {'memory' => '2048', 'cpus' => 2, 'ip' => '10', 'provision' => 'Workpress.yaml'}
}
  
  Vagrant.configure('2') do |config|
  
    config.vm.box = 'ubuntu/bionic64'
    config.vm.box_check_update = false
  
    vms.each do |name, conf|
      config.vm.define "#{name}" do |m|
        m.vm.hostname = "#{name}.ansible.local"
        m.vm.network 'private_network', ip: "172.27.11.#{conf['ip']}"
  
        m.vm.provider 'virtualbox' do |vb| # VirtualBox
          vb.memory = conf['memory']
          vb.cpus = conf['cpus']
        end
		
		m.vm.provision 'ansible_local' do |ansible|
          ansible.playbook = "#{conf['provision']}"
		  ansible.version = "latest"
        end
	end
end
end