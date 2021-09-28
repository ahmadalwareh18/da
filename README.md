# DirectAdmin Installation

This documentation is dedicated to helping in DirectAdmin control panel installation on VPS servers running CentOS 7 and doing required configuration. <br>
<i>You can refer to the official installation website for help from <a href="https://www.directadmin.com/installguide.php">here</a></i>

## Installation

Use the package manager [yum](https://wiki.centos.org/PackageManagement/Yum) to install the required packages (<b><i>Only for <a href="https://help.directadmin.com/item.php?id=354">CentOS 7</a></i></b>).

```bash
yum install vim wget gcc gcc-c++ flex bison make bind bind-libs bind-utils openssl openssl-devel perl quota libaio \
libcom_err-devel libcurl-devel gd zlib-devel zip unzip libcap-devel cronie bzip2 cyrus-sasl-devel perl-ExtUtils-Embed \
autoconf automake libtool which patch mailx bzip2-devel lsof glibc-headers kernel-devel expat-devel \
psmisc net-tools systemd-devel libdb-devel perl-DBI perl-Perl4-CoreLibs perl-libwww-perl xfsprogs rsyslog logrotate crontabs file kernel-headers
```

## Downloading and installing DA panel 
```bash
#Download the setup script
wget https://www.directadmin.com/setup.sh

#Make the Script executable
chmod 755 setup.sh

#Run the Script with Auto mode
./setup.sh auto

#Reference: https://docs.directadmin.com/getting-started/installation/installguide.html
```

## Adding SSL certificate to CP website

```bash
#Change directory to where SSL script is located
cd /usr/local/directadmin/scripts

#Create request with 4096-bit key encryption
./letsencrypt.sh request_single <domain-name-here> 4096

#Change to directadmin directory
cd /usr/local/directadmin

#Activate SSL parameter in DA options
./directadmin set ssl 1

#Certificate root key setting
./directadmin set carootcert /usr/local/directadmin/conf/carootcert.pem

#Setting redirect for hostname
./directadmin set ssl_redirect_host <domain-name-here>  #If you got error try adding it manaully in /usr/local/directadmin/conf/directadmin.conf

#Restarting directadmin service
service directadmin restart

#Reference: https://help.directadmin.com/item.php?id=629
```

## CP default port custmization

```bash
#Edit directadmin.conf using vim
vim /usr/local/directadmin/conf/directadmin.conf

#Set port as requried, or try adding it manaully
port=9806

#Restarting directadmin service
service directadmin restart
```

## Change FTP service to proftpd

```bash
#Change to directadmin directory
cd /usr/local/directadmin/custombuild

#Perform update to components
./build update

#Set FTP server to proftpd
./build set ftpd proftpd

#Build proftpd service
./build proftpd

#Edit default port
vim /etc/proftpd.conf

#########################
port        2005
#Save with !wq

#Restarting proftpd service
service proftpd restart
```

