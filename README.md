# iotCamera
Iot Camera project

## Getting Started

###  Hardware

- Raspberry Pi Zero W Starter Kit ()
- Camera Module
- SD Card (min 8 GB)

### Installing 
- Download Raspian Stretch Lite https://downloads.raspberrypi.org/raspbian_lite_latest
- Write Image of Raspian to SD Card with https://sourceforge.net/projects/win32diskimager/files/latest/download
- plug in sd Card in Pi
- Connect Pi to Monitor, Keyboard and power adapter

### Raspian first Steps

- Log in with: ```shell pi ``` 
- password: raspberry
- Changing Your Password: sudo password
- change settings for WIFI and ssh: sudo raspi-config
- update software: sudo apt-get update, sudo apt-get upgrade

### Installing motionEye

- Install ffmpeg and v4l-utils: sudo apt-get install ffmpeg v4l-utils -y
- Install libmariadbclient18 and libpq5 required by motion: sudo apt-get install libmariadbclient18 libpq5 -y
- Install motion: sudo wget https://github.com/Motion-Project/motion/releases/download/release-4.1/pi_stretch_motion_4.1-1_armhf.deb
                  sudo dpkg -i pi_stretch_motion_4.1-1_armhf.deb
- Install the dependencies from the repositories: sudo apt-get install python-pip python-dev libssl-dev libcurl4-openssl-dev libjpeg-dev   -y
- Install motioneye globally: sudo -H pip install motioneye
- Prepare the configuration directory:  sudo mkdir -p /etc/motioneye
                                        sudo cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf
- Prepare the media directory: sudo mkdir -p /var/lib/motioneye
- Add an init script, configure it to run at startup and start the motionEye server:
  sudo cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service
  sudo systemctl daemon-reload
  sudo systemctl enable motioneye
  sudo systemctl start motioneye
  
### Show status of motioneye

- sudo systemctl status motioneye
  

