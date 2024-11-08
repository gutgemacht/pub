sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
Crontab:
sfdisk -d /dev/nvme0n1 > /home/sokol/Dropbox/Linux/sokol-g5.partition_tablei_dev_nvme0n1.txt


vi /etc/default/grub
update-grub 
apt-get remove --purge plymouth -y
sudo apt remove --purge libreoffice* -y
sudo apt remove --purge *games* -y
update-initramfs -u


add-apt-repository universe
sudo apt install mono-runtime p7zip-full p7zip-rar python3-launchpadlib -y

sudo apt autoremove

curl -fsSL https://www.naps2.com/naps2-public.pgp | sudo gpg --dearmor -o /etc/apt/keyrings/naps2.gpg
echo "deb [signed-by=/etc/apt/keyrings/naps2.gpg] https://downloads.naps2.com ./" | sudo tee /etc/apt/sources.list.d/naps2.list >/dev/null
sudo apt update
sudo apt install naps2

apt-get install flatpak preload timeshift gdebi gparted mc nwipe xpaint ttf-mscorefonts-installer
sudo fc-cache -fv
sudo apt install gnome-shell-extension-desktop-icons-ng
gnome-extensions enable ding@rastersoft.com

sudo apt install numix-gtk-theme

backup the system!
sudo apt-get install jpegoptim
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
sudo apt-get install ubuntu-restricted-extras vlc gufw
sudo apt-get install clamtk clamav clamav-freshclam chromium-codecs-ffmpeg-extra

flatpak install flathub org.chromium.Chromium -y ;
flatpak install flathub com.skype.Client -y ;
flatpak install flathub us.zoom.Zoom -y ; 
flatpak install flathub org.telegram.desktop -y ;
flatpak install flathub org.keepassxc.KeePassXC -y ;
flatpak install flathub org.mozilla.firefox -y --user sokol;
flatpak install flathub com.system76.Popsicle -y ;
flatpak install flathub org.mozilla.Thunderbird -y ;
flatpak install flathub com.thincast.client -y ;
flatpak install flathub com.anydesk.Anydesk -y ;
flatpak install flathub com.google.Chrome -y
flatpak install flathub com.skype.Client -y
flatpak install flathub org.onlyoffice.desktopeditors -y
flatpak install flathub com.github.dail8859.NotepadNext -y
apt-get remove pluma

#sudo apt install usb-creator-gtk
Virtualbox:
deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian jammy contrib
wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmor --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg
sudo usermod -g vboxusers sokol
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo apt-get install virtualbox


VeraCrypt:
sudo add-apt-repository ppa:unit193/encryption
sudo apt-get install veracrypt 

Gnome:
sudo apt-get install compizconfig-settings-manager

# CIFS
apt-get install cifs-utils
mkdir /mnt/fritzbox
sudo mount -t cifs -o username=fritz1 //fritz.nas/FRITZ.NAS/Volume/FRITZ /mnt/fritzbox/
/fritz.nas/FRITZ.NAS/Volume/FRITZ /mnt/fritzbox/ cifs username=sokol,password=Netcool11!! 0 0

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
sudo apt install mono-devel gtk-sharp2 libappindicator0.1-cil libmono-2.0-1

dpkg -l | grep linux-image
apt-get remove "kernel"


sudo apt remove --autoremove snapd
sudo apt-get clean
sudo apt-get autoremove
sudo apt remove nano

Video on external mon:
sudo cp ~/.config/monitors.xml /var/lib/gdm3/.config/
sudo cp /home/sokol/.config/monitors.xml /var/lib/lightdm/

#sudo apt remove tracker tracker-extract tracker-miner-fs

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
systemctl enable ufw

sudo apt-get --purge autoremove
