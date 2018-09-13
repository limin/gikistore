This assumes you have Nginx and Node.js installed. Take a backup of existing configuration before modifying so you can rollback if things go wrong.

    Go to location where Nginx is installed (default on UNIX based OS like CentOS/Ubuntu would be /etc/nginx)
    Go to sites-available
    Create a new file with the following (for easy understanding you can name the file as your domain name)

upstream backend {
server localhost:3000;
}

server {
listen 80;
server_name siterelic.com;

root /var/tools/public;

location / {
try_files $uri @backend;
}

location @backend {
proxy_pass http://backend;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header Host $host;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
# Following is necessary for Websocket support
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
}
}

There is the five crucial block above, let me go through one-by-one.

    Upstream â specify the variable as âbackendâ and give node.js server & port information. In an example, Iâve given localhost:3000 that means I am running node.js on the same server as Nginx with 3000 port number.
    Server â give the port number, which Nginx should be listening on, and server name as your domain name.
    Root â the directory from where you want to serve the static files.
    Location â this is important. I am asking Nginx to try looking for files in specified directory with root location and if it doesnât match then go to @backend which is node.js
    Location@backend â this is generic node.js+websocket.io proxy configuration

Enable the site in /etc/nginx/sites-enabled by creating a symbolic

    cd /etc/nginx/sites-enabled
    ln -s /etc/nginx/sites-available/$yourdomainname .

### Restart the Nginx and have fun!
```
sudo systemctl restart nginx
```
or 
```
sudo service nginx restart
```

## Reference
* [https://geekflare.com/nginx-static-files-node-js/](https://geekflare.com/nginx-static-files-node-js/)