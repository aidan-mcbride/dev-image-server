# Base image
FROM nginx

# remove default nginx config
RUN rm /etc/nginx/conf.d/default.conf

# copy new config
COPY nginx.conf /etc/nginx/conf.d/

# copy index.html
COPY index.html /usr/share/nginx/html/
