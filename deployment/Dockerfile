FROM nginx:latest

# Replace 'nginx.conf' with your own configuration file if needed
# use with ssl or without ssl uncomment which nginx configuration file you want to use 

COPY nginx.conf /etc/nginx/nginx.conf 
# COPY nginxssl.conf /etc/nginx/nginx.conf

# COPY html /usr/share/nginx/html
COPY ssl /ssl


EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
