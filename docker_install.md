# Install docker:

Uninstall old versions
Older versions of Docker went by the names of docker, docker.io, or docker-engine. Uninstall any such older versions before attempting to install a new version:

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
 Set up the repository
Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
 sudo apt-get update
 sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
 ```   
Add Docker’s official GPG key:

```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
Use the following command to set up the repository:

```
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
Install Docker Engine
Update the apt package index:

```
 sudo apt-get update
 ```
 ```
  sudo chmod a+r /etc/apt/keyrings/docker.gpg
 sudo apt-get update
 ```
 Install Docker Engine, containerd, and Docker Compose.

Latest
Specific version

To install the latest version, run:

```
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Verify that the Docker Engine installation is successful by running the hello-world image:

```
 sudo docker run hello-world
 ```
This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.
