FROM nginx:alpine

LABEL maintainer="samuel.gratzl@datavisyn.io"

ENV PHOVEA_API_SERVER=api
ENV PHOVEA_NGINX_PORT=80
COPY ./deploy/web/nginx-default.conf /etc/nginx/conf.d/default.conf
CMD sed -i -e "s/PHOVEA_API_SERVER/${PHOVEA_API_SERVER-api}/g" /etc/nginx/conf.d/default.conf && sed -i -e "s/PHOVEA_NGINX_PORT/${PHOVEA_NGINX_PORT-api}/g" /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'
COPY ./bundles /usr/share/nginx/html
COPY ./deploy/web/*.html /usr/share/nginx/html/
