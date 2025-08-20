# debian12
debian12 ye kurduğum sunucular

<img width="1276" height="800" alt="Ekran Görüntüsü - 2025-08-20 21-52-38" src="https://github.com/user-attachments/assets/edf6e8aa-c6a9-433a-a17f-4c8586e5220f" />

Isp Config 3.2 yi kuarken kullandıgım kodlar

sudo apt update && sudo apt upgrade -y
sudo apt install -y wget curl

wget -O - https://get.ispconfig.org | sudo sh -s -- \
  --use-apache \
  --use-php=default \
  --use-ftp=pureftpd \
  --use-mail=dovecot \
  --use-dns=bind \
  --use-mysql \
  --no-web \
  --interactive

sudo apt --fix-broken install -y
sudo apt autoremove -y
sudo apt clean

sudo hostnamectl set-hostname server1.ahba.com
sudo nano /etc/hosts 
