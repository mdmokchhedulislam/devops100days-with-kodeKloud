
task: 
Day by day traffic is increasing on one of the websites managed by the Nautilus production support team. Therefore, the team has observed a degradation in website performance. Following discussions about this issue, the team has decided to deploy this application on a high availability stack i.e on Nautilus infra in Stratos DC. They started the migration last month and it is almost done, as only the LBR server configuration is pending. Configure LBR server as per the information given below:



a. Install nginx on LBR (load balancer) server.


b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf.


c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers.


d. Once done, you can access the website using StaticApp button on the top bar.







1. Installed Nginx on the LBR Server

I installed Nginx using the system’s package manager and ensured the service was enabled and running:

sudo yum install nginx -y   # (For CentOS/RHEL)
sudo systemctl enable nginx
sudo systemctl start nginx

3. Configure Nginx Load Balancing (MAIN CONFIG FILE ONLY)
/etc/nginx/nginx.conf

sudo vi /etc/nginx/nginx.conf




http {
    upstream app_servers {
        server 172.16.238.10;
        server 172.16.238.11;
        server 172.16.238.12;
    }

    server {
        listen 80;
        server_name _;

        location / {
            proxy_pass http://app_servers;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }
}

