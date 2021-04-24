FROM registry.access.redhat.com/ubi8:8.1
ARG A_HTTP_PROXY
ARG A_HTTPS_PROXY
ENV http_proxy=${A_HTTP_PROXY}
ENV https_proxy=${A_HTTPS_PROXY}
RUN yum -y install nginx
RUN sed -i 's:user nginx;:#user nginx;:g' /etc/nginx/nginx.conf
RUN sed -i 's:listen       80 default_server;:listen       8080 default_server;:g' /etc/nginx/nginx.conf
RUN sed -i 's/:80/:8080/g' /etc/nginx/nginx.conf
RUN     chown -R nginx:nginx /var/log/nginx && \
        chown -R nginx:nginx /etc/nginx/conf.d && \
        chown -R nginx:nginx /var/lib/nginx/tmp
RUN touch /var/run/nginx.pid && \
        chown -R nginx:nginx /var/run/nginx.pid
USER 998
ENTRYPOINT ["nginx", "-g", "daemon off;"]
