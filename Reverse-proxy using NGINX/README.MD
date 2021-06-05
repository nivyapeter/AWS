# REVERSE PROXY AND LOAD BALANCER
## Reverse proxy by using NGINX

- Launch two instances in ec2 and install nginx
- In first ec2 instance make an index.html in the location /var/www/html -> where default html file is located
- Go to the location cd /etc/nginx/sites-available and copy default file into new file in the same location using the following command:
   - sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/mysite.conf
- Create a soft link for this mysite.conf file to sites-enabled default file using the following command:
   - ln -s /etc/nginx/sites-available/mysite.conf /etc/nginx/sites-enabled/default
- Edit this mysite.conf file and add loacation block in that file by following:
```
   -  location /app1/ {
                proxy_pass http://13.235.67.122/;
        }
```
  -   the ip given here is the ip address of second instance
- Reload nginx using following command:
    - sudo nginx -s reload
- Type the first instance ip/app1 like following
   -http://15.206.70.72/app1/
-This will direct to second instance page