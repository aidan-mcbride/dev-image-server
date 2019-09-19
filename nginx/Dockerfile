# Base image
FROM nginx

# remove default nginx config
RUN rm /etc/nginx/conf.d/default.conf

# copy new config
COPY nginx.conf /etc/nginx/conf.d/

# copy index.html
COPY index.html /usr/share/nginx/
# copy css + bg image
COPY css /usr/share/nginx/css/
COPY background.jpg /usr/share/nginx/

# # copy images
# COPY images /usr/share/nginx/images/
