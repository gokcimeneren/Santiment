### Friends, all the details are in your e-mail, so I'm moving on to the installation without explanation:

#

### Equipment:
> We don't need much equipment right now, we're just applying, but here's my own equipment:

> 4 CPU 8 RAM Ubuntu 22.04 

#

### Setup

```console
# update and docker installation
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

```console
# required configurations:
sudo mkdir -p /opt/sanchain/readonly
cd /opt/sanchain/readonly

sudo git clone https://github.com/santiment/sanr-pos-network.git .

sudo mv env.example .env
sudo nano .env

# EXTERNAL_IP=Sunucunun IP adresini giriniz - CTRL X Y ENTER ile çıkınız.
sudo ln -s docker-compose-readonly.yml docker-compose.yml
sudo docker compose up -d
```

> When the installation is successful, we apply [here](https://nodes.sanr.network/)

![image](https://github.com/ruesandora/santiment/assets/101149671/96d60c17-eb2a-4a18-8cd0-4a9a1f1e23da)

> If you have problems, you can use VPN, but I still wouldn't give it mobile data etc. more logical.


