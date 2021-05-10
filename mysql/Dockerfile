FROM mysql:8

RUN ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo "Asia/Shanghai" > /etc/timezone && chown -R mysql:root /var/lib/mysql/


CMD ["mysqld"]