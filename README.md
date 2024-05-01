
# Nginx Setup in Ubuntu




## Installing Nginx

To install Nginx, use following command:-

```bash
sudo apt update
sudo apt install nginx
```

To check nginx is running or not:-

```bash
sudo systemctl status nginx.service
```

## Status check

![App Screenshot](https://github.com/Itsmrhashtag/nginx_tutorial/blob/main/Screenshot%20from%202024-05-01%2012-12-25.png?raw=true)

## Test
check from `localhost:80`

![App Screenshot](https://github.com/Itsmrhashtag/nginx_tutorial/blob/main/Screenshot%20from%202024-05-01%2012-04-14.png?raw=true)
## Creating our own website

```bash
cd /var/www
sudo mkdir new
cd new
```

## Create index.html file
```bash
sudo nano index.html
```
Paste the following in `index.html` save it by clicking `ctrl+S` and exit by `ctrl+X`:-
```bash
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>Hello, Nginx!</title>
</head>
<body>
    <h1>Hello, Nginx!</h1>
    <p>We have just configured our Nginx web server on Ubuntu Server!</p>
</body>
</html>
```
## Setting up virtual host
To set up virtual host, we need to create file in `/etc/nginx/sites-enabled/` directory.
```bash
cd /etc/nginx/sites-enabled
```
### Create file

```bash
sudo nano new
```
### Paste following in file save it by clicking `ctrl+S` and exit by `ctrl+X`

```bash
server {
       listen 81;
       listen [::]:81;

       server_name localhost;

       root /var/www/tutorial;
       index index.html;

       location / {
               try_files $uri $uri/ =404;
       }
}
```
## Activating virtual host and testing results
Restart Nginx service
```bash
sudo systemctl restart nginx.service
```

check from `localhost:81`

![App Screenshot](https://github.com/Itsmrhashtag/nginx_tutorial/blob/main/Screenshot%20from%202024-05-01%2012-35-21.png?raw=true)
