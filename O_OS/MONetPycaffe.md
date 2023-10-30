Raspbian OS

## 1.Preinstall

### 1.1 Download the Raspberry Pi Imager (RPI)

the red GUI installer on the official website

### 1.2 Choose Other Raspberry Pi OS
Raspberry Pi OS (Legacy, 64-bit), 2023-05-03 Version
the Debian Bullseye and desktop

> so far, seems Raspberry Pi all chosen the Debian as the sources.lists
> By the way, the Bullseye 2023-05-03 which support Python 3.9 (compatible with the pytorch aarch64 version)

### 1.3 erase and install on the SD card

## 2.Start the raspberry Pi OS

### 2.1 Find the Raspberry Pi configuration 

1. Enable the SSH
2. Enable the VNC

### 2.2 Basic apt install and Change the source files

```python
sudo apt update
sudo apt upgrade
```

1. Raspberry Pi
change the raspberry pi 
```sh
sudo nano /etc/apt/sources.list.d/raspi.list
```

Then, edit the source list to the mirror you want

2. Debian 
```sh
sudo nano /etc/apt/sources.list
```

Then, edit the source list to the mirror you want

```sh
sudo apt update
sudo apt upgrade
```

### 2.3 Apt install xrdp and docker-compose 

```sh
sudo apt install xrdp
sudo apt install docker-compose
```

>  Hint: the docker-compose will install docker and docker-compose at the same time, which is one-click convenience


Check the docker and docker-compose version
```sh
docker --version
docker-compose --verison
```

### 2.4 PIP Virtualenv

Install pip virtual environment
```sh
pip install virtual pipenv
```


Install pip venv
```sh
python -m venv yolo
```

> Hint: the python (CHANGABLE, used the system python, which is python3.9. If your raspbian are too new as python 3.11, you may need to re-install) 
-m (DO NOT CHANGE, Namespace, argparse configuration)
venv (DO NOT CHANGE, Namespace, argparse configuration)
yolo (CHANGABLE, you can change yolo to the name you want)


activate the pip venv
```sh
source yolo/bin/activate
```

Output 
There will appear `(yolo)` before the command line if activate succeed
```
(yolo)pi@raspberry:
```


### 2.5 follow this Blog
Which is excellent guide on Raspberry Pi Installation
https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html

TODO (write the guide according to the blog) 

## 3 How to use

### 3.1 Check the yolo folder is under your current path
Type ls to see whether the yolo folder is under your current path
```sh
ls
```

Output
There shall be a folder named yolo



### 3.2 Activate the venv
Using source to activate
```sh
source yolo/bin/activate
```

Output 
There will appear `(yolo)` before the command line if activate succeed
```
(yolo)pi@raspberry:
```

### 3.3 Check the pytorch 
type python into python environment
```python
python
>>import pytorch
>>torch.__version__
```

Output
The output shall include the torch version 

Press `Ctrl+Z` to exit and do the other command you want





## Reference
1.

https://github.com/HinTak/RaspberryPi-Dev/blob/master/Downgrading-Pi-Kernel.md

2. 

https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html

3.

There is no Raspberry Pi 32-bit wheel available due to unsupported libraries.

https://github.com/Qengineering/PyTorch-Raspberry-Pi-64-OS

4\. the Raspbian OS needs v8a 64bit to install pytorch

the 32 bit is not compatible with the pytorhc

and the 202305 64 bit version which carried by raspberry pi own installer seems OK

5\. Update my kernel

https://raspberrypi.stackexchange.com/questions/120735/kernel-version-does-not-update-when-using-apt-update-apt-full-upgrade