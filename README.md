yiimp

Install script for yiimp on Ubuntu 16.04

While I did add some server security to the script, it is every server owners responsibility to fully secure their own servers. After the installation you will still need to customize your serverconfig.php file to your liking, add your API keys, and build/add your coins to the control panel.

There will be several wallets already in yiimp. These have nothing to do with the installation script and are from the database import from the yiimp github.

If you need further assistance we have a small but growing discord channel at https://discord.gg/

Do not run the script as root

This script has an interactive beginning and will ask for the following information:

Your time zone Server Name Support Email Address Server Admin Email Address If you would like fail2ban installed If you would like to have SSL (LetsEncrypt) installed - Your domain must be pointed to your server prior to running the script or SSL will fail to install. New custom location for yiimp admin login.

Once those questions are answered the script will then be fully automated for the rest of the install.

Update and Upgrade Ubuntu Packages
Install Aptitude
Install and configure Nginx
Install MariaDB with random root password
Install php7
Install various dev packages required for building blocknotify and stratum
Install SendMail
Install Fail2Ban if selected
Install and configur phpmyadmin with random password for phpmyadmin user
Clone yiimp build packages, create directory structure, set file permissions, and more
Update server clock
Install LetsEncrypt if selected
Create yiimp database, create 2 users with random passwords - passwords saved in ~/.my.cnf
Import the sql dumps from yiimp
Create base yiimp serverconfig.php file to get you going
Updates all directory permissions
This install script will get you 95% ready to go with yiimp. There are a few things you need to do after the main install is finished.

You must update the following files:

/var/web/serverconfig.php - update this file to include your public ip to access the admin panel. update with public keys from exchanges. update with other information specific to your server..
/etc/yiimp/keys.php - update with secrect keys from the exchanges.
After you add the missing information to those files then run: bash main.sh bash loop2.sh bash block.sh

To download and run

git clone https://github.com/bitebivip/yiimp_install_scrypt.git

cd yiimp_install_scrypt

bash install.sh

after installation you must create an debug.log file in /var/log/debug.log and set all premissions to allow

then set crontabs for main.sh loop2.sh and blocks.sh, wallets and your algos @ reboot like this

crontab -e

(editor 2)

@reboot /var/web/main.sh

@reboot /var/web/loop2.sh

@reboot /var/web/blocks.sh

and your algo you want to start

@reboot /var/stratum/run.sh skunk

@reboot /var/stratum/run.sh x11

@reboot /var/stratum/run.sh scrypt

save it and reboot !

then only add your Coins and set it in admin panel

If this helped you or you feel giving please donate BTC Donation:

Feel free to join our Discord channel at https://discord.gg/

Antiico
