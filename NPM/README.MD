## NPM
# INSTALLATION OF NPM
- create a directory called repo in home directory ( mkdir repo)
- clone the link 
      git clone https://github.com/Prakhil-tp/test-server.git
- cd test-server/
- npm install      ( for installing npm :  curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash , then  . ~/.nvm/nvm.sh , nvm install 4.4.5 , node -e "console.log('Running Node.js ' + process.version)"
then type npm install )

- npm start	  


# How do I run a single command at startup using systemd?

        - cd /etc/systemd/systemd/system
		- create a file as hello.service
		- sudo vi hello.service
```		
[Unit]
Description =index.js
After = network.target
[Service]
WorkingDirectory=/home/ubuntu/repo/test-server
Environment=NODE_PORT=8000
Type=simple
User=ubuntu
Restart=on-failure
ExecStart=/home/ubuntu/.nvm/versions/node/v4.4.5/bin/node /home/ubuntu/repo/test-server/index.js
[Install]
WantedBy = multi-user.target

```

			
        -  sudo systemctl enable npm.service
        -  sudo systemctl start npm.service
		-  sudo systemctl status npm.service
		- curl localhost:8000
		- curl localhost:8000/digest
		
		
		
- create an AMI from the above instance and create a new instance from that AMI
- then run curl localhost:8000
- same o/p will get as before.		
- while giving the security group the http should have the security group of vpn
		


