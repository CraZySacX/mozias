FROM mariadb
ENV MYSQL_DATABASE=moziasdb MYSQL_USER=mozias
COPY ./config/db/database.sql /docker-entrypoint-initdb.d/database.sql