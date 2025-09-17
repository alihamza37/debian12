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
ISPConfig, Linux tabanlı sunucular için geliştirilmiş açık kaynaklı bir hosting kontrol panelidir.

Web tabanlı arayüz üzerinden

    Web sunucusu (Apache/Nginx)
    E-posta sunucusu (Postfix, Dovecot)
    DNS sunucusu (Bind, PowerDNS)
    FTP sunucusu (Pure-FTPd, vsftpd)
      Veritabanı yönetimi (MySQL/MariaDB)
    SSL (Let’s Encrypt) ayarları
    Kullanıcı/Hosting paketleri yönetimi gibi servisleri tek bir yerden yönetmeyi sağlar.

NodeBB kurulum

sudo apt update && sudo apt upgrade -y
sudo apt install -y curl git build-essential nginx mariadb-server mariadb-client redis-server
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
sudo systemctl enable mariadb redis-server nginx
sudo systemctl start mariadb redis-server nginx
sudo mysql -e "CREATE DATABASE IF NOT EXISTS nodebb CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
sudo mysql -e "CREATE USER IF NOT EXISTS 'nodebbuser'@'localhost' IDENTIFIED BY 'debian123';"
sudo mysql -e "GRANT ALL PRIVILEGES ON nodebb.* TO 'nodebbuser'@'localhost';"
sudo mysql -e "FLUSH PRIVILEGES;"
cd /var/www
sudo git clone -b v3.x https://github.com/NodeBB/NodeBB.git nodebb
cd nodebb
sudo chown -R $USER:$USER .
npm install --production

<img width="1276" height="790" alt="Ekran Görüntüsü - 2025-09-16 21-01-11" src="https://github.com/user-attachments/assets/9a221012-9917-4347-9564-c9c5d8488a36" />

NodeBB ne işe yarar

İnsanların konu açıp tartışma yapabileceği, soru sorup cevap verebileceği bir topluluk platformu sağlar.
Gerçek zamanlı çalışır: Bildirimler, mesajlar ve yanıtlar anlık olarak görünür.
Eklentiler ve temalar ile özelleştirilebilir.
Kullanıcılar arasında özel mesajlaşma, profil sayfaları, sosyal medya girişi gibi özellikler sunar.
Linux üzerinde Nginx, Redis, MongoDB/MariaDB gibi servislerle entegre çalışır.
