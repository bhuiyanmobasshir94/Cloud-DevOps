```
version: "3.6"

volumes:
  mysqldata:

services:
  db:
    image: mysql:latest        
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    volumes:
      - ./mysqldata:/var/lib/mysql          
      - ./mysqldata/init.sql:/docker-entrypoint-initdb.d/init.sql
    environment:
      - MYSQL_DATABASE=${MYSQL_DB_NAME-dev}
      - MYSQL_USER=${MYSQL_USER-dev}
      - MYSQL_ROOT_PASSWORD=${MYSQL_PASSWORD-dev}
    ports:
      - ${MYSQL_PORT-3306}:3306

  adminer:
    image: adminer:latest
    ports:
      - ${ADMINER_PORT-8082}:8080
```
```
version: '3.2'
services:
    db:
        image: mysql:5.7

        restart: always
        environment:
          MYSQL_ROOT_PASSWORD: myUserPass
          MYSQL_DATABASE: mydb
          MYSQL_USER: myUser
          MYSQL_PASSWORD: myUser

    phpmyadmin:
        depends_on:
          - db
        image: phpmyadmin/phpmyadmin
        restart: always
        ports:
          - 8088:80
        environment:
          PMA_HOST: db
          MYSQL_ROOT_PASSWORD: myUserPass
```
```
version: "3.1"
volumes:
  mysqldata:
services:
  db:
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: dev
    ports:
      - 3306:3306 
    volumes:
      - ./mysqldata:/var/lib/mysql
  adminer:
    image: adminer
    restart: always
    ports:
      - 8882:8080
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - 8883:80
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: dev
```
          

- [1](https://geshan.com.np/blog/2022/02/mysql-docker-compose/)
