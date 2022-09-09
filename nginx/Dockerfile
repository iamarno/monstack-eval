# use a fixed version of nginx
ARG NGINX_VERSION="1.23.1"

FROM nginx:$NGINX_VERSION

# remove default nginx config to avoid funky leaks
RUN rm /etc/nginx/conf.d/default.conf
RUN rm /etc/nginx/nginx.conf
# copy default html and custom config
COPY html /usr/share/nginx/html
COPY conf/nginx.conf /etc/nginx/
COPY conf/grafana.conf /etc/nginx/conf.d
# copy ssl cert
#COPY ssl/fullchain1.pem /etc/nginx/ssl/
#COPY ssl/privkey1.pem /etc/nginx/ssl/
