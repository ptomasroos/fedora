# Home

This is the installation guide how to install Fedora according to my regular setup conventions.

## update

```
sudo dnf -y update
```

## tools

```
sudo dnf -y install git tig htop
sudo dnf -y install https://github.com/atom/atom/releases/download/v1.0.11/atom.x86_64.rpm
```
## vmware tools

This will remove the open vm tools and install proprietary vmware tools for enhanced experience in vmware workstation make sure that the disc is inserted via the UI

```
sudo dnf -y remove open-vm*
cd /tmp/
cp /run/media/*/VMware\ Tools/VMwareTools-9.9.2-2496486.tar.gz /tmp
tar -zxvf VMwareTools*.tar.gz
sudo ./vmware-tools-distrib/vmware-install.pl --default EULA_AGREED=yes
sudo reboot
```

## i3

Installing the I3 Window Manager and making sure to insert correct configuration

```
sudo dnf -y install i3 i3status i3-doc
cd ~
mkdir .i3
wget https://raw.githubusercontent.com/ptomasroos/home/master/.i3/config -O .i3/config
sudo reboot
```


## oh-my-zsh
```
sudo dnf -y install zsh
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
sudo reboot
```

## go

```
cd /tmp/
wget https://storage.googleapis.com/golang/go1.5.1.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go*.tar.gz
```

## node

```
curl -sL https://rpm.nodesource.com/setup | bash -
sudo yum install -y nodejs
```

# dotfiles
```
cd ~
wget https://raw.githubusercontent.com/ptomasroos/home/master/.zshrc -O .zshrc
sudo reboot
```
