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


