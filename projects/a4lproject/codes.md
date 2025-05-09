export DBName='a4lwordpress'
export DBUser='a4lwordpress'
export DBPassword='a4lwordpress'
export DBRootPassword='a4lwordpress'

sudo yum install -y mariadb105-server httpd
sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2 

mysqladmin -u root password $DBRootPassword 

sudo systemctl enable httpd
sudo systemctl start httpd
sudo systemctl enable mariadb
sudo systemctl start mariadb

sudo wget http://wordpress.org/latest.tar.gz -P /var/www/html

cd /var/www/html

sudo tar -zxvf latest.tar.gz

sudo cp -rvf wordpress/* .


sudo rm -R wordpress
 sudo rm latest.tar.gz 
 sudo cp ./wp-config-sample.php ./wp-config.php
 //nano wp-config
//wp-config-sample.php  wp-config.php         
 //nano wp-config.php 
 sudo sed -i "s/'database_name_here'/'$DBName'/g" wp-config.php 
 
 sudo sed -i "s/'username_here'/'$DBUser'/g" wp-config.php 
 sudo sed -i "s/'password_here'/'$DBPassword'/g" wp-config.php 
 //nano wp-config.php 
 sudo chown apache:apache * -R
 echo "CREATE DATABASE $DBName;" >> /tmp/db.setup
 echo "CREATE USER '$DBUser'@'localhost' IDENTIFIED BY '$DBPassword';" >> /tmp/db.setup
 echo "CREATE USER '$DBUser'@'localhost' ^C >> /tmp/db.setup
 echo "GRANT ALL ON $DBName.* TO '$DBUser'@'localhost';" >> /tmp/db.setup
 echo "FLUSH PRIVILEGES;" >> /tmp/db.setup 
 sudo mysql -u root --password=$DBRootPassword < /tmp/db.setup
 
 
 
 
 
 
 echo "CREATE DATABASE $DBName;" >> /tmp/db.setup
echo "CREATE USER '$DBUser'@'%' IDENTIFIED BY '$DBPassword';" >> /tmp/db.setup
echo "GRANT ALL ON $DBName.* TO '$DBUser'@'%';" >> /tmp/db.setup
echo "FLUSH PRIVILEGES;" >> /tmp/db.setup
mysql -h a4lwordpress.c4dgwy4cg8oz.us-east-1.rds.amazonaws.com -u $DBUser --password="$DBRootPassword" < /tmp/db.setup

sudo rm /tmp/db.setup


//sudo dnf install -y php php-mysqlnd php-fpm

//sudo nano /etc/update-motd.d/40-cow
sudo echo "#!/bin/sh" > /etc/update-motd.d/40-cow
sudo echo "cowsay "amazon linux 2 hiiiiii"" >> /etc/update-motd.d/40-cow

sudo rm /etc/update-motd.d/30-banner
sudo update-motd



sudo yum install -y amazon-efs-utils
sudo mkdir /etc/wp-content
sudo nano /etc/fstab
fs-07f46af037dd9f475:/ /etc/wp-content efs _netdev,tls,iam 0 0

sudo mount /etc/wp-content/


echo '#!/bin/sh' | sudo tee /etc/update-motd.d/40-cow


also, make sure you have security group 2049 added.
make sure that an iam role with efs is allowed.
you cant edit the cowsay without echo '#!/bin/sh' | sudo tee /etc/update-motd.d/40-cow
