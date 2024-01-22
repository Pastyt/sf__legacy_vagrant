Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"

  config.vm.provision "shell", inline: <<-SHELL
    sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
      wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
      sudo apt-get update
      sudo DEBIAN_FRONTEND=noninteractive apt-get -yq install postgresql-8.4
      sudo -u postgres psql -c "CREATE USER myuser WITH PASSWORD 'mypassword';"
      sudo -u postgres psql -c "CREATE DATABASE mydatabase WITH OWNER myuser;"
  SHELL

end
