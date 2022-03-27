FROM quay.io/wildfly/wildfly
RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#70365 --silent
RUN curl https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.28/mysql-connector-java-8.0.28.jar -O
RUN mkdir -p wildfly/modules/system/layers/base/com/mysql/main
RUN mv mysql-connector-java-8.0.28.jar wildfly/modules/system/layers/base/com/mysql/main
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]

#1 - ./opt/jboss/wildfly/jboss-cli.sh -c
#2 - module add --name=com.mysql --resources=/opt/jboss/wildfly/modules/system/layers/base/com/mysql/main/mysql-connector-java-8.0.28.jar --dependencies=javax.api,javax.transaction.api
#3 - /subsystem=datasources/jdbc-driver=mysql:add(driver-name=mysql,driver-module-name=com.mysql)
#4 - data-source add --jndi-name=java:/MySqlDS --name=MySQLPool --connection-url=jdbc:mysql://172.20.0.2:3306/sample --driver-name=mysql --user-name=mysql --password=mysql


#COPY startup-config.cli /opt/jboss/startup-scripts/startup-config.cli
#COPY include/standalone/configuration/ /opt/jboss/wildfly/standalone/configuration/
#RUN module add --name=com.mysql --resources=mysql-connector-java-8.0.28.jar --dependencies=javax.api,javax.transaction.api
#RUN /subsystem=datasources/jdbc-driver=mysql:add(driver-name=mysql,driver-module-name=com.mysql)

#data-source add --jndi-name=java:/MySqlDS --name=MySQLPool --connection-url=jdbc:mysql://172.17.0.2:3306/mysqlschema --driver-name=mysql --user-name=jboss --password=jboss

