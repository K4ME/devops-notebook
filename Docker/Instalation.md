Source: [wsl2-docker-quickstart](https://github.com/codeedu/wsl2-docker-quickstart/blob/main/README.en.md#docker-engine-docker-native-directly-installed-on-wsl2)

### Instalation on Windows

Considering that Docker was made natively to run in a Linux environment, for better operation on Windows
It is highly recommended to use WSL 2.

#### What is WSL2
In 2016, Microsoft announced the possibility of running Linux within Windows 10 as a subsystem
and this was called WSL or Windows Subsystem for Linux.

#### Instalation of WSL 2

##### Windows Update
Verify if your Windows is updated, because the WSL 2 depende de uma versão atualizada do Hyper-V. 
Verify the Windows Update.

##### Update the WSL

Running the version 2004 of Windows 10 or Windows 11, the WSL is already on your machine, 
execute the command to catch the most recently version of WSL:
````shell
wsl --update
````

##### Assign the default version of WSL to version 2

WSL version 1 may be the default on your machine, run the command below to set version 2 as the default:
````shell
wsl --set-default-version 2
````

##### Install Ubuntu

Run the command:
````shell
wsl --install
````


### Install Docker with Docker Engine (Docker Native)
The installation of Docker on WSL 2 is identical to the installation of Docker on your own Linux distribution, so if you have Ubuntu, it's the same as Ubuntu, if it's Fedora, it's the same as Fedora. The installation documentation for Docker on Linux by distribution is here, but let's see how to install it on Ubuntu.

For those who are migrating from Docker Desktop to Docker Engine, we have two options:

Uninstall Docker Desktop.
Disable the Docker Desktop service in Windows services. This option allows you to use Docker Desktop if necessary, but for most users, uninstalling Docker Desktop is the recommended approach. If you choose the second option, you will need to delete the file ~/.docker/config.json and authenticate with Docker again using the command "docker login".
If you need to integrate Docker with IDEs other than VSCode

VSCode already integrates with Docker on WSL through the Remote WSL or Remote Container extension.

You need to enable the connection to the Docker server via TCP. Here are the steps:

Create the file /etc/docker/daemon.json: sudo echo '{"hosts": ["tcp://0.0.0.0:2375", "unix:///var/run/docker.sock"]}' > /etc/docker/daemon.json
Restart Docker: sudo service docker restart
After this procedure, go to your IDE and to connect to Docker, choose the TCP Socket option and put the URL http://WSL-IP:2375. Your WSL IP can be found with the command cat /etc/resolv.conf.

If it doesn't work, restart WSL with the command wsl --shutdown and start the Docker service again.

##### Install the prerequisites:
````shell
sudo apt update && sudo apt upgrade
sudo apt remove docker docker-engine docker.io containerd runc
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
````

##### Add the Docker repository to the list of sources in Ubuntu:
````shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
````

##### Intall Docker Engine
````shell
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
````

##### Grant permission to run Docker with your current user:
````shell
sudo usermod -aG docker $USER
````

##### Start Docker service:
````shell
sudo service docker start
````

This above command will need to be executed every time Linux is restarted. If the Docker service is not running, it will show this error message when running the docker command:

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
The Docker Compose installed now will be in version 2, to run it instead of docker-compose use docker compose.

Error starting Docker in Ubuntu 22.04
If even after starting the Docker service, the following error or a similar one occurs:

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running? Run the command sudo update-alternatives --config iptables and choose option 1 iptables-legacy

Run sudo service docker start again. Run some Docker command such as docker ps to verify if it is working correctly. If it does not show the error above, it is OK.

#### Tip for Windows 11
In Windows 11, you can specify a default command to be executed whenever WSL is started. This allows us to automatically start the docker service. 
Edit the file /etc/wsl.conf:

Run the command to edit:
````shell
sudo vim /etc/wsl.conf
````

Press the letter i and paste the contents:

````shell
[boot]
command="service docker start" 
Press the : key, type wq to save/exit and press enter. Done, restart WSL with the wsl --shutdown command in DOS or PowerShell to test. After opening WSL again, type the docker ps command to check if the command doesn't return the following message: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
````
