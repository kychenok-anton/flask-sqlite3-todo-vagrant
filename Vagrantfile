Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.synced_folder ".", "/vagrant"

  config.vm.provision "shell", inline: <<-SHELL
    # Оновлення пакетів і установка Python
    apt-get update
    apt-get install -y python3 python3-pip python3-venv

    cd /vagrant

    python3 -m venv venv

    ./venv/bin/pip install --upgrade pip

    ./venv/bin/pip install -r requirements.txt
  SHELL
end
