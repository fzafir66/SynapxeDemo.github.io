# Use the official Nginx image as the base
FROM nginx:alpine
# Create directories and set permissions
RUN mkdir -p /var/cache/nginx/client_temp /var/cache/nginx/proxy_temp /var/cache/nginx/fastcgi_temp /var/cache/nginx/uwsgi_temp /var/cache/nginx/scgi_temp \
    && chmod -R 777 /var/cache/nginx /var/run /var/log/nginx /etc/nginx/nginx.conf /etc/nginx/conf.d

# Adjust Nginx to listen on port 8080 instead of 80 (non-root users can't bind to ports below 1024)
RUN sed -i 's/listen\(.*\)80;/listen 8080;/g' /etc/nginx/conf.d/default.conf /etc/nginx/nginx.conf

# Copy static content to the Nginx server
COPY . /usr/share/nginx/html

# Run as non-root user
USER 1001

# Expose port 8080 for the service
EXPOSE 8080
