Vagrant.configure("2") do |config|
  config.vm.box = "debian12"
    config.vm.box_url = "file://#{Dir.pwd}/debian12.box" # força caminho da vm
  # Port forwarding para expor as portas 30001 e 30002 do guest para host
  config.vm.network "forwarded_port", guest: 30001, host: 30001
  config.vm.network "forwarded_port", guest: 30002, host: 30002

  # Rede pública com bridge (interface física)
  config.vm.network "public_network", bridge: "enp2s0"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2

    # Configurações para resolver DNS corretamente via NAT
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # Provisionamento (shell)
  config.vm.provision "shell", inline: <<-SHELL
    echo "Executando Ansible playbook dentro da VM..."

    # Forçar resolver DNS temporariamente (opcional, só para garantir)
    echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

    sudo apt update
    sudo apt install -y ansible nginx

    sudo systemctl start nginx
    sudo systemctl status nginx

    ansible-playbook /vagrant/ansible/setup_kubernetes.yml -i localhost,
  SHELL
end


#
