# WildFly-MySQL-DockerCompose

## Build

Build with Docker compose

```
$ docker-compose build
```

Run with Docker compose

```
$ docker-compose up
```

When the server is up and running you need to add 
database drivers and datasource through the Command Line Interface.

Enter the running server through Docker Bash

```
$ docker exec -it <Wildfly container id> bash
```

then navigate to bin-folder
```
$ cd /opt/jboss/wildfly/bin/
```

Enter the Command Line Interface

```
$ ./jboss-cli.sh -c
```

Add mysql module
```
$ module add --name=com.mysql --resources=/opt/jboss/wildfly/modules/system/layers/base/com/mysql/main/mysql-connector-java-8.0.28.jar --dependencies=javax.api,javax.transaction.api
```
install the MySQL JDBC driver
```
$ /subsystem=datasources/jdbc-driver=mysql:add(driver-name=mysql,driver-module-name=com.mysql)
```
Add your datasource (the internal ip adress might be different, find it with 'docker inspect <database container>)

```
$ data-source add --jndi-name=java:/MySqlDS --name=MySQLPool --connection-url=jdbc:mysql://172.20.0.2:3306/sample --driver-name=mysql --user-name=mysql --password=mysql
```

The internal ip adress might be different, find it with:
```
docker inspect <database container>
```

