FROM mysql:8.0.33
#set env variable for db name and password
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"
# copy the sql schema 
ADD db_backup.sql docker-entrypoint-initdb.d/db_backup.sql