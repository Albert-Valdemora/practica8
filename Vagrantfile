Vagrant.configure("2") do |config|
  # Configurar la VM
  config.vm.box = "ubuntu/bionic64"  # Usa la caja de Ubuntu 18.04
  
  # Asignar recursos
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"  # Asignar 512MB de RAM
    vb.cpus = 1        # Asignar 1 CPU
  end
  
  # Configurar red y carpeta compartida
  config.vm.network "forwarded_port", guest: 80, host: 8080  # Redireccionar puerto
  config.vm.synced_folder "./html", "/var/www/html"  # Compartir carpeta local con Apache
  
  # Configurar servidor Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end
