✅ Nagios Core Installation Commands



# 1. System Update & Install Required Dependencies
sudo apt-get update -y
sudo apt-get install -y apache2 apache2-utils autoconf gcc libc6 libgd-dev make php python3 tree unzip wget libkrb5-dev openssl libssl-dev

# 2. Download Nagios Core from Official Website
cd /tmp
wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.5.0.tar.gz

# 3. Extract the Tar File
tar -zxf nagios-4.5.0.tar.gz
cd nagios-4.5.0

# 4. Configure and Compile
sudo ./configure --with-httpd-conf=/etc/apache2/sites-enabled/
sudo make all

# 5. Install Core Components
sudo make install-groups-users
sudo make install
sudo make install-daemoninit
sudo make install-commandmode
sudo make install-config
sudo make install-webconf

# 6. Create Nagios User and Set Password
sudo passwd nagios

# 7. Add www-data to Nagios Group
sudo usermod -a -G nagios www-data

# 8. Enable Apache Modules
sudo a2enmod cgi
sudo a2enmod rewrite

# 9. Setup Web Access for Nagios
sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin

# 10. Verify Nagios Configuration
sudo /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

# 11. Restart Apache and Nagios
sudo systemctl restart nagios
sudo systemctl restart apache2



✅ Nagios Plugin Installation Commands



# 1. Download Nagios Plugins
cd /tmp
wget https://nagios-plugins.org/download/nagios-plugins-2.4.0.tar.gz

# 2. Extract the Plugin Tar File
tar -zxf nagios-plugins-2.4.0.tar.gz
cd nagios-plugins-2.4.0

# 3. Install Required Dependencies
sudo apt-get install -y automake autotools-dev bc build-essential dc gawk gettext libmcrypt-dev libnet-snmp-perl libssl-dev snmp

# 4. Configure, Compile and Install Plugins
sudo ./configure
sudo make
sudo make install

# 5. Verify Plugins Installation
ls -l /usr/local/nagios/libexec/









