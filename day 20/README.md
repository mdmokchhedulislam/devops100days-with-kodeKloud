The Nautilus application development team is planning to launch a new PHP-based application, which they want to deploy on Nautilus infra in Stratos DC. The development team had a meeting with the production support team and they have shared some requirements regarding the infrastructure. Below are the requirements they shared:



a. Install nginx on app server 3 , configure it to use port 8092 and its document root should be /var/www/html.


b. Install php-fpm version 8.2 on app server 3, it must use the unix socket /var/run/php-fpm/default.sock (create the parent directories if don't exist).


c. Configure php-fpm and nginx to work together.


d. Once configured correctly, you can test the website using curl http://stapp03:8092/index.php command from jump host.

NOTE: We have copied two files, index.php and info.php, under /var/www/html as part of the PHP-based application setup. Please do not modify these files.



answer ++++++++++++++++

1. login server3 and install nginx
2. configure nginx from  sudo vi /etc/nginx/nginx.conf
3. run command: sudo yum install -y php php-fpm

4. create socket directory: sudo mkdir -p /var/run/php-fpm
5. sudo vi /etc/opt/remi/php82/php-fpm.d/www.conf
6. listen = /var/run/php-fpm/default.sock
listen.owner = nginx
listen.group = nginx
listen.mode = 0660

7. restart php: 
sudo systemctl restart php-fpm
sudo systemctl enable php-fpm


