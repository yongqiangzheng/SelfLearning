sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

安装驱动重启
sudo ubuntu-drivers autoinstall
reboot
安装CUDA
wget https://developer.download.nvidia.com/compute/cuda/11.3.0/local_installers/cuda_11.3.0_465.19.01_linux.run


下载代理工具
wget -O clash.gz https://github.com/Dreamacro/clash/releases/download/v1.11.4/clash-freebsd-amd64-v1.11.4.gz
gzip -f clash.gz -d # -d：解压
chmod +x clash #提权
./clash
cd ~/.config/clash
wget -O config.yaml <订阅连接>
wget -O Country.mmdb https://www.sub-speeder.com/client-download/Country.mmdb #全球ip库
./clash


下载安装vscode
https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64
sudo dpkg -i code_1.69.2-1658162013_amd64.deb


下载安装google chrome
https://www.google.com/intl/zh-CN/chrome/
sudo dpkg -i google-chrome-stable_current_amd64.deb