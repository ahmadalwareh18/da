# DirectAdmin Installation

This documentation is dedicated to helping in DirectAdmin control panel installation on VPS servers running CentOS 7 and doing required configuration. 
## Installation

Use the package manager [yum](https://wiki.centos.org/PackageManagement/Yum) to install the required packages.

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

Reference: https://docs.directadmin.com/getting-started/installation/installguide.html
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
