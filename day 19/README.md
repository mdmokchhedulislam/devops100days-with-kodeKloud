xFusionCorp Industries is planning to host two static websites on their infra in Stratos Datacenter. The development of these websites is still in-progress, but we want to get the servers ready. Please perform the following steps to accomplish the task:



a. Install httpd package and dependencies on app server 3.


b. Apache should serve on port 8083.


c. There are two website's backups /home/thor/blog and /home/thor/games on jump_host. Set them up on Apache in a way that blog should work on the link http://localhost:8083/blog/ and games should work on link http://localhost:8083/games/ on the mentioned app server.


d. Once configured you should be able to access the website using curl command on the respective app server, i.e curl http://localhost:8083/blog/ and curl http://localhost:8083/games/

answer +++++++++++++++++++

1. need to go app server 3 and login 
2. run command: sudo yum install -y httpd
3. update port: sudo vi /etc/httpd/conf/httpd.conf

4. make dir /var/www/html/blog
5. make dir /var/www/html/games
6. copy blog : scp -r thor@jump_host:/home/thor/blog /tmp/


7. copy games: scp -r thor@jump_host:/home/thor/games /tmp/

8. sudo cp -r /tmp/blog/* /var/www/html/blog/
sudo cp -r /tmp/games/* /var/www/html/games/


9. change permission: sudo chown -R apache:apache /var/www/html/blog
sudo chown -R apache:apache /var/www/html/games

10. restart apache: sudo systemctl restart httpd





