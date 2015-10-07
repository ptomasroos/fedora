# Home

This is the installation guide how to install Fedora according to my regular setup conventions.

![Image of desktop](https://raw.githubusercontent.com/ptomasroos/home/master/screenshot.png)

## update

Prefer to run this update proceedure through text-mode (e in grub + run level 3 at the end). The reason is I got a bunch of problem when trying to upgrade all packages through gnome.

```
sudo dnf -y update
```

## vmware tools

This will remove the open vm tools and install proprietary vmware tools for enhanced experience in vmware workstation make sure that the disc is inserted via the UI

```
sudo dnf -y remove open-vm*
cd /tmp/
cp /run/media/*/VMware\ Tools/VMwareTools*.tar.gz /tmp
tar -zxvf VMwareTools*.tar.gz
sudo ./vmware-tools-distrib/vmware-install.pl --default EULA_AGREED=yes
sudo reboot
```

## tools

```
sudo dnf -y install git tig htop vim autojump autojump-zsh
cd /tmp
wget https://github.com/atom/atom/releases/download/v1.0.11/atom.x86_64.rpm
sudo dnf -y install atom*.rpm
```

## i3

Installing the I3 Window Manager and making sure to insert correct configuration

```
sudo dnf -y install i3 i3status
cd ~
mkdir .i3
wget https://raw.githubusercontent.com/ptomasroos/home/master/.i3/config -O .i3/config
sudo reboot
```


## oh-my-zsh
```
sudo dnf -y install zsh
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
cd ~
wget https://raw.githubusercontent.com/ptomasroos/home/master/.zshrc -O .zshrc
sudo reboot
```

## go

```
cd /tmp/
wget https://storage.googleapis.com/golang/go1.5.1.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go*.tar.gz
```

## node
Regular install with 
```
curl -sL https://rpm.nodesource.com/setup | bash -
sudo yum install -y nodejs
```
does not work with Fedora 21 + 22. Use manual installation below instead

```
sudo dnf -y install https://rpm.nodesource.com/pub_0.12/fc/22/x86_64/nodejs-0.12.7-1nodesource.fc22.x86_64.rpm
```

## intellij

```
cd /tmp/
wget https://download.jetbrains.com/idea/ideaIC-14.1.4.tar.gz
tar -zxvf idea*.gz
rm idea*.gz
sudo mv idea* /opt/idea
sudo ln -s /opt/idea/bin/idea.sh /usr/local/bin/idea
```

## sublime
```
cd /tmp/
wget https://gist.githubusercontent.com/simonewebdesign/8507139/raw/bb380e1fb290f75458ec8aa8ec8ba2e1f259d81f/install_sublime_text.sh
chmod +x install_sublime_text.sh
sudo ./install_sublime_text.sh
```

## mysql
```
sudo dnf install \
  https://dev.mysql.com/get/mysql-community-release-fc22-5.noarch.rpm \
  mysql-community-server mysql-workbench-community

sudo systemctl enable mysqld
sudo service mysqld start
```

## dotfiles
```
cd ~
sudo reboot
```
