# Kira network

## [Official site](https://kira.network)

### 1. Установка зависимостей:

```
sudo apt update && sudo apt -y upgrade  
sudo apt install -y network-manager  
sudo apt update  
sudo apt install -y apt-transport-https ca-certificates curl gnupg lsb-release  
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg  
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \  
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null  
sudo apt update  
sudo apt install -y docker-ce docker-ce-cli containerd.io
```  

### 2. Создание sudoer пользователя

```
sudo useradd kira -m -s /bin/bash  
sudo passwd kira  
sudo usermod -aG sudo kira
```  

### 3.Установка ноды Kira  

```sudo su - kira  
sudo -s
```  

#### Запускаем скрипт установки  

```
cd /tmp && read -p "Input branch name: " BRANCH && \  
wget https://raw.githubusercontent.com/KiraCore/kira/$BRANCH/workstation/init.sh -O ./i.sh && \  
chmod 555 -v ./i.sh && H=$(sha256sum ./i.sh | awk '{ print $1 }') && read -p "Is '$H' a [V]alid SHA256 ?: "$'\n' -n 1 V && \  
[ "${V,,}" != "v" ] && echo "INFO: Setup was cancelled by the user." || ./i.sh "$BRANCH"
```


For delete old node and install new:

To completely uninstall Docker:

Step 1

```
dpkg -l | grep -i docker
```

To identify what installed package you have:

Step 2

```
sudo apt-get purge -y docker-engine docker docker.io docker-ce docker-ce-cli docker-compose-plugin
sudo apt-get autoremove -y --purge docker-engine docker docker.io docker-ce docker-compose-plugin
```  

The above commands will not remove images, containers, volumes, or user created configuration files on your host. If you wish to delete all images, containers, and volumes run the following commands:

```
sudo rm -rf /var/lib/docker /etc/docker

sudo rm /etc/apparmor.d/docker

sudo groupdel docker

sudo rm -rf /var/run/docker.sock
```  

You have removed Docker from the system completely.

For remove user and f userfolder:

```
sudo deluser --remove-home kira
```



