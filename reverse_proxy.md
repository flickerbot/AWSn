reverse proxy on nginx 

We are doing thi stest on nodejs application so we will be installing nodejs and starting the app.js using node app.js 


sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm


Install Nginx 

> goto /etc/nginx/sites-avaliable


```

server {
   listen 80;
   listen 443 ;
 
    server_name <rishiraj.nsb08.cloud>; # public ip of the server


    location / {
        proxy_pass http://localhost:8080; # Assuming your Node.js app is running on port 3000
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }

}

```


make a file in sites-avaliable named server and paste the following code ,here we are sayin to load our 8080 port when the url is requested 




Save this configuration in an Nginx server block file, typically located in the /etc/nginx/sites-available/ directory. Then, create a symbolic link to enable the configuration:

> sudo ln -s /etc/nginx/sites-available/your-config-file /etc/nginx/sites-enabled/


Finally, test the Nginx configuration and restart Nginx:

> sudo nginx -t 
> sudo systemctl restart nginx



#installing ssl certification using letsencrypt

update the above file 

```

server {
    listen 80;
    listen 443 ssl; # Listen on port 443 for HTTPS traffic
    server_name rishiraj.nsb08.cloud;

    ssl_certificate /path/to/your_domain.crt; # Replace with the actual path to your SSL certificate file
    ssl_certificate_key /path/to/your_domain.key; # Replace with the actual path to your SSL private key file

    location / {
        proxy_pass http://localhost:8080; # Assuming your Node.js app is running on port 8080
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

```
now we will be installing the certbot python and it will do our task like magic ;>

> sudo apt install certbot python3-certbot-nginx

> sudo certbot --nginx -d example.com -d www.example.com


replace example.com with our dns

###https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04 








