FROM nginx
# remove the default nginx config file
RUN rm -rf /etc/nginx/conf.d/default.conf
# copy the new config file
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf