#!/usr/bin/env bash
# Configure Nginx server to have a custom 404 page that contains the string Ceci n'est pas une page

# Install nginx
sudo apt-get update
sudo apt-get install -y nginx

# Creating Sample Page
echo "Hello World!" > /var/www/html/index.html

# add the following configuration to the existing server block
string_for_replacement="server_name _;\n\trewrite ^\/redirect_me https:\/\/www.google.com permanent;"
sudo sed -i "s/server_name _;/$string_for_replacement/" /etc/nginx/sites-enabled/default

# code for error page and redirect error 404
echo "Ceci n'est pas une page" > /var/www/html/404.html
string_for_replacement="listen 80 default_server;\n\terror_page 404 \/404.html;\n\tlocation = \/404.html {\n\t\troot \/var\/www\/html;\n\t\tinternal;\n\t}"
sudo sed -i "s/listen 80 default_server;/$string_for_replacement/" /etc/nginx/sites-enabled/default

# Restart Nginx
service nginx restart
