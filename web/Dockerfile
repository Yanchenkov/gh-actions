FROM nginx:1.18-alpine
ENV NGINX_ENTRYPOINT_QUIET_LOGS=0

RUN rm /usr/share/nginx/html/index.html
COPY . /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
