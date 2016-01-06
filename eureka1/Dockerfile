FROM jeanblanchard/tomcat:8

MAINTAINER Daniel Giribet 'dani@calidos.cat'

ENV EUREKA_VERSION 1.3.5

# remove default configuration so there is no admin user
#ADD tomcat-users.xml /opt/tomcat/conf/

RUN cd /opt/tomcat/webapps && \
  mkdir eureka && \
  cd eureka && \
  wget -q http://repo1.maven.org/maven2/com/netflix/eureka/eureka-server/${EUREKA_VERSION}/eureka-server-${EUREKA_VERSION}.war && \
  jar xf eureka-server-${EUREKA_VERSION}.war && \
  rm eureka-server-${EUREKA_VERSION}.war
RUN curl http://repo1.maven.org/maven2/com/netflix/blitz4j/blitz4j/1.36.1/blitz4j-1.36.1.jar \
  -o /opt/tomcat/webapps/eureka/WEB-INF/lib/blitz4j-1.36.1.jar

ADD config.properties /opt/tomcat/webapps/eureka/WEB-INF/classes/config.properties
ADD eureka-client-test.properties /opt/tomcat/webapps/eureka/WEB-INF/classes/eureka-client-test.properties
ADD eureka-server-test.properties /opt/tomcat/webapps/eureka/WEB-INF/classes/eureka-server-test.properties
  
EXPOSE 8080

ENTRYPOINT ["/opt/tomcat/bin/catalina.sh"]

CMD ["run"]
