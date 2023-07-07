# deploy_nodejs


[1] update ubuntu server
$ sudo apt-get update

[2] Install Node.js and NPM
$ sudo apt-get install nodejs
$ sudo apt-get install npm

[3] Check the installed versions
$ node -v
$ npm -v

[4] Clone your project from Git or copy it to the server

[5] Navigate to the project directory
$ cd /var/www/gpt-node/

[6] Install project dependencies
$ npm install

[7] Start your project
$ npm start

[8] Install PM2 globally using NPM
$sudo npm install pm2 -g

[9] Navigate to your project directory
$ cd /var/www/gpt-node/

[10] Start your Node.js application with PM2
$ pm2 start app.js

[11] Verify that your application is running
$ pm2 status

[12] If you want to stop your application
$ pm2 stop app_name

[13] If you want to restart your application
$ pm2 restart app_name

[14] If you want to delete your application
$ pm2 delete app_name

[15] If you want to monitor your application logs
$ pm2 logs app_name

[16] Install nginx, which is a popular web server that can act as a reverse proxy for your Node.js application
$ sudo apt update
$ sudo apt install nginx

[17] Configure nginx as a reverse proxy for your Node.js application. First, create a new nginx configuration file
$ sudo nano /etc/nginx/sites-available/gpt-node
 
[18] Paste the following configuration into the file
server {
    listen 80;
    server_name gpt.kawalsidang.org;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

[19] Enable the new nginx configuration by creating a symbolic link to it in the sites-enabled directory
$ sudo ln -s /etc/nginx/sites-available/gpt-node /etc/nginx/sites-enabled/

[20] Test the nginx configuration and restart the nginx service
$ sudo nginx -t
$ sudo systemctl restart nginx
