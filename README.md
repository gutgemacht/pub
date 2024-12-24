sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
Crontab:
sfdisk -d /dev/nvme0n1 > /home/sokol/Dropbox/Linux/sokol-g5.partition_tablei_dev_nvme0n1.txt


vi /etc/default/grub
update-grub 
apt-get remove --purge plymouth -y
sudo apt remove --purge libreoffice* -y
sudo apt remove --purge *games* nano tracker tracker-extract tracker-miner-fs -y
update-initramfs -u


#add-apt-repository universe
# p7zip-full p7zip-rar ttf-mscorefonts-installer
apt install curl mono-runtime python3-launchpadlib flatpak preload timeshift gdebi gparted mc nwipe xpaint gnome-shell-extension-desktop-icons-ng jpegoptim clamtk clamav clamav-freshclam vlc gufw compizconfig-settings-manager dirmngr software-properties-common apt-transport-https lsb-release ca-certificates vim
sudo fc-cache -fv
gnome-extensions enable ding@rastersoft.com
sudo apt autoremove

curl -fsSL https://www.naps2.com/naps2-public.pgp | sudo gpg --dearmor -o /etc/apt/keyrings/naps2.gpg
echo "deb [signed-by=/etc/apt/keyrings/naps2.gpg] https://downloads.naps2.com ./" | sudo tee /etc/apt/sources.list.d/naps2.list >/dev/null
sudo apt update
sudo apt install naps2


sudo apt install numix-gtk-theme unattended-upgrades
echo 'APT::Periodic::Update-Package-Lists "1";' >> /etc/apt/apt.conf.d/50unattended-upgrades
echo 'APT::Periodic::Unattended-Upgrade "1";' >> /etc/apt/apt.conf.d/50unattended-upgrades


flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.dropbox.Client -y
flatpak install flathub org.chromium.Chromium -y 
flatpak install flathub com.skype.Client -y 
flatpak install flathub us.zoom.Zoom -y ; 
flatpak install flathub org.telegram.desktop -y
flatpak install flathub org.keepassxc.KeePassXC -y 
flatpak install flathub org.mozilla.firefox -y 
flatpak install flathub com.system76.Popsicle -y 
flatpak install flathub org.mozilla.Thunderbird -y 
flatpak install flathub com.thincast.client -y 
flatpak install flathub com.anydesk.Anydesk -y 
flatpak install flathub com.google.Chrome -y
flatpak install flathub com.skype.Client -y
flatpak install flathub org.onlyoffice.desktopeditors -y
flatpak install flathub com.github.dail8859.NotepadNext -y

Virtualbox:
deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian jammy contrib
wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmor --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg
sudo usermod -g vboxusers sokol
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo apt-get install virtualbox -y


VeraCrypt:
curl -fsSL https://notesalexp.org/debian/alexp_key.asc | gpg --dearmor | sudo tee /usr/share/keyrings/alexp_key.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/alexp_key.gpg] https://notesalexp.org/debian/$(lsb_release -sc)/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/alexp.list
apt get update
sudo apt-get install veracrypt 

sudo apt-get clean
sudo apt-get autoremove

backup the system!



#############################
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
sudo apt install mono-devel gtk-sharp2 libappindicator0.1-cil libmono-2.0-1

dpkg -l | grep linux-image
apt-get remove "kernel"


sudo apt remove --autoremove snapd


sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable ssh
sudo ufw enable
systemctl enable ufw

sudo apt-get --purge autoremove



# CIFS
apt-get install cifs-utils
mkdir /mnt/fritzbox
sudo mount -t cifs -o username=fritz1 //fritz.nas/FRITZ.NAS/Volume/FRITZ /mnt/fritzbox/
/fritz.nas/FRITZ.NAS/Volume/FRITZ /mnt/fritzbox/ cifs username=USER1111,password=12345!! 0 0


