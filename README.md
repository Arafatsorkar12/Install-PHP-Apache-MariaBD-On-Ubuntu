# Install-PHP-Apache-MariaBD-On-Ubuntu



//------------------------------------------------------------------//
//                          INSTALL APACHE                          //
//------------------------------------------------------------------//

```php
sudo apt update
sudo apt install apache2
sudo ufw app list
sudo ufw allow in "Apache"
sudo ufw status

sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl stop apache2
sudo systemctl restart apache2
```

//------------------------------------------------------------------//
//                             INSTALL PHP                          //
//------------------------------------------------------------------//

```php
sudo apt-get update
sudo apt install php libapache2-mod-php php-mysql  //Install Default PHP

PHP 8.2
sudo apt install php8.2 libapache2-mod-php8.2 php8.2-common php8.2-sqlite3 php8.2-curl php8.2-fpm php8.2-dev php8.2-curl php8.2-xmlrpc php8.2-gd php8.2-mysql php8.2-mbstring php8.2-xml php8.2-soap php8.2-cli php8.2-zip php8.2-bz2 php8.2-dba php8.2-imap php8.2-intl php8.2-ldap php8.2-cli php8.2-cgi php8.2-fpm php8.2-mcrypt



sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt -y install php7.4
sudo apt-get install -y php7.4-cli php7.4-json php7.4-common php7.4-mysql php7.4-zip php7.4-gd php7.4-mbstring php7.4-curl php7.4-xml php7.4-bcmath

```
//------------------------------------------------------------------//
//                         INSTALL MARIADB                          //
//------------------------------------------------------------------//

```php
sudo apt update
sudo apt install mariadb-server
sudo systemctl start mariadb.service
sudo mysql_secure_installation


//CREATE OR SET PASSWORD
sudo mysql

Set Password:
	FLUSH PRIVILEGES;
	ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';

SET All Access , Not Nessesary

	GRANT ALL ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
	GRANT ALL ON laravel_db.* TO 'laravel_user'@'localhost';
```

//------------------------------------------------------------------//
//                      INSTALL PHPMYADMIN                          //
//------------------------------------------------------------------//

```php
sudo apt install phpmyadmin

sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl

sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin.conf
sudo systemctl reload apache2.service


//------------------------------------------------------------------//
//     			ERROR FIX ON MULTI PHP ON PHPMYADMIN                //
//------------------------------------------------------------------//
One more thing for the top answer; need to add

Include /etc/phpmyadmin/apache.conf
to

/etc/apache2/apache2.conf

and restart Apache:

/etc/init.d/apache2 restart

```

//------------------------------------------------------------------//
//     						Install Composer    		            //
//------------------------------------------------------------------//


```php
curl -sS https://getcomposer.org/installer | php

sudo mv composer.phar /usr/local/bin/composer

sudo chmod +x /usr/local/bin/composer

```
//------------------------------------------------------------------//
//     			Configure Apache to serve Laravel 		            //
//------------------------------------------------------------------//


```php

To host a Laravel site, it is necessary to configure the Apache web server, and for this purpose, you must launch the virtual host file:

sudo vim /etc/apache2/sites-available/laravel.conf

<VirtualHost *:80>
ServerName example.com
ServerAdmin admin@example.com
DocumentRoot /var/www/html/laravelapp/public
<Directory /var/www/html/laravelapp>
AllowOverride All
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

sudo a2ensite laravel.conf

sudo a2enmod rewrite

sudo systemctl restart apache2






sudo a2enmod php8.3
sudo a2dismod php7.x
sudo service apache2 restart

```

//-------------------------------------------//
      Defolt out run 
//-------------------------------------------//

```php      
  /usr/bin/php8.3 artisan serve
```
