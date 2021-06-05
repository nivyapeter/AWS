## NGINX AS A LOAD BALANCER(In Ubuntu)
1. Launch three instances in ec2 and install nginx in three
2. Take first ec2 instance as load balancer
3. In all three do the following steps:
    - uname -n | sudo tee /var/www/html/index.html
    - cat !$
4. Go to the location cd /etc/nginx/sites-available and copy default file into new file in the same location using the following command:
   - sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/load_balancer.conf
5.   Create a soft link for this mysite.conf file to sites-enabed default file using the following command:
   - ln -s /etc/nginx/sites-available/load_balancer.conf /etc/nginx/sites-enabled/default
6. Edit this load_balancer.conf with the following commands:

```
    upstream web_backend {
      server 13.235.114.105;
      server 13.126.205.139;
      }
      server {
              listen 80;
              location / {
                      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                      proxy_pass http://web_backend;
              }
            }
```
 * the ip address given here are the ip address of the other two ec2 instances
7. Reload the configuration file using the following commands:
    - sudo nginx -s reload
8. Type the following commands:
   curl localhost:
 - This give the output with changing ip address



