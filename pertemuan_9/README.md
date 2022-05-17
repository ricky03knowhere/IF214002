# Instalasi Docker, Mysql & Dbeaver (Windows 11)

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-9)
- ⚡Instalasi Docker & Mysql
- ⚡Instalasi DBeaver

## WSL2 activation
- Windows Search >> Turn Windows Features on / off
  
  ✅ Virtual Machine, Windows Hypervisor, Windows subsystem

    ![img](./Screenshot%202022-05-17%20141237.png)

- WSL2 update package

  Link : [https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

- Set default version

  ```shell 
  wsl --set-default-version 2
  ```

- Download Linux Distro at Windows Store 
  ![img](./Screenshot%202022-05-17%20142537.png)

- Errors & Solution

  - Error : 

    ```shell 
    WslRegisterDistribution failed with error: 0xffffffff Error: 0xffffffff (null)
    ```

  - Solution :

    - Bukan Powershell as administrator, Cari apakah ada port 53 yang sudah berjalan.
    
      ```shell 
      netstat -a -o -n 
      ```
      
      ![img](Screenshot%202022-05-17%20143304.png)

    - Matikan proses yang berjalan: 

      ```shell
      taskkill /f /pid [PID]
      ```

      ![img](./Screenshot%202022-05-17%20143359.png)

- Linux Distro berhasil diinstal

  ![img](./Screenshot%202022-05-17%20143647.png)


## Docker Instalation

- Download & Install Docker Desktop

  Link : [https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe)

- Verify Instalation
  ```shell
  docker version
  ```
  ![img](./Screenshot%202022-05-17%20150223.png)

- Docker Info
  ```shell
  docker info
  ```
  ![img](./Screenshot%202022-05-17%20150814.png)

- Instal Mysql
  ```shell
  docker pull mysql
  docker image list
  ```
  ![img](./Screenshot%202022-05-17%20151123.png)

## DBeaver Instalation
- Donwload Dbeaver for windows

  Link : [https://dbeaver.io/files/dbeaver-ce-latest-x86_64-setup.exe](https://dbeaver.io/files/dbeaver-ce-latest-x86_64-setup.exe)

- Run Dbeaver
  
  ![img](./Screenshot%202022-05-17%20153624.png)
