FROM quay.io/wildfly/wildfly
RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#70365 --silent
RUN curl https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.28/mysql-connector-java-8.0.28.jar -O
RUN mkdir -p wildfly/modules/system/layers/base/com/mysql/main
RUN mv mysql-connector-java-8.0.28.jar wildfly/modules/system/layers/base/com/mysql/main
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]



#COPY startup-config.cli /opt/jboss/startup-scripts/startup-config.cli
#COPY include/standalone/configuration/ /opt/jboss/wildfly/standalone/configuration/
#RUN module add --name=com.mysql --resources=mysql-connector-java-8.0.28.jar --dependencies=javax.api,javax.transaction.api
#RUN /subsystem=datasources/jdbc-driver=mysql:add(driver-name=mysql,driver-module-name=com.mysql)


