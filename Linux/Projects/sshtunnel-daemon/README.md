# SSH Tunnel

## Description
![SSH Tunnel](https://raw.githubusercontent.com/koss822/misc/master/imgs/sshtunnel.png "SSH Tunnel diagram")

* Allow you to tunnel remote targets through multiple ssh servers
* Clients can connect to your ssh tunnel gateway on your local network
* Easy configuration (YAML)
* Easy and secure installation (Docker)

## Settings

~~~~
main:
  listen: 0.0.0.0
tunnels:
  - remote: username@remote_ip
    ports:
      # ssh
      - local: 2000 # This has to match docker-compose file
        remote_target: localhost
        remote_port: 22
~~~~

## Installation

1. Install Ubuntu (or other Linux)

2. Install docker
~~~~
sudo apt install docker.io
~~~~

3. Add your user to docker group (do not forget to relogin)
~~~~
sudo usermod -a -G docker your_username
~~~~

4. Install docker compose
~~~~
sudo apt install curl
sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
~~~~

5. Generate ssh-keys
~~~~
cd settings
ssh-keygen -f ./id_rsa
~~~~

6. Edit `settings/sshtunnel.yml`
7. Edit `docker-compose.yml`
8. Run `docker-compose build`
9. Try `docker-compose up` (after CTRL-C)
10. Run `docker-compose up -d` (it should start after restart)
