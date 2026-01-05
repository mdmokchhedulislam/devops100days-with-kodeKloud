xFusionCorp Industries is planning to host a WordPress website on their infra in Stratos Datacenter. They have already done infrastructure configuration—for example, on the storage server they already have a shared directory /vaw/www/html that is mounted on each app host under /var/www/html directory. Please perform the following steps to accomplish the task:



a. Install httpd, php and its dependencies on all app hosts.


b. Apache should serve on port 3002 within the apps.


c. Install/Configure MariaDB server on DB Server.


d. Create a database named kodekloud_db8 and create a database user named kodekloud_cap identified as password LQfKeWWxWD. Further make sure this newly created user is able to perform all operation on the database you created.


e. Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App


answer ++++++++++++++++++

1. login all apphost like stapp01, stapp01 and stapp03 

2.run command: sudo yum install -y httpd php php-mysqlnd php-gd php-xml php-mbstring

3.apache configure :sudo vi /etc/httpd/conf/httpd.conf -> listen port 3002

4.apache start: sudo systemctl start httpd
sudo systemctl enable httpd

5. restart apache: sudo systemctl restart httpd

6. install maria db: sudo yum install -y mariadb-server

7. enable and start : sudo systemctl start mariadb
sudo systemctl enable mariadb


8.create database: 
CREATE DATABASE kodekloud_db8;
CREATE USER 'kodekloud_cap'@'%' IDENTIFIED BY 'LQfKeWWxWD';
GRANT ALL PRIVILEGES ON kodekloud_db8.* TO 'kodekloud_cap'@'%';
FLUSH PRIVILEGES;

9. last exit




