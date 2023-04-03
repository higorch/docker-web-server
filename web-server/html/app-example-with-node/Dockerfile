FROM higorch/node18.15.0-nginx-for-frontend

WORKDIR /var/www/html/app-example-with-node

COPY . .

COPY .docker/nginx/nginx.conf /etc/nginx

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]