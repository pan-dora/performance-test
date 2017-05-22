FROM tomcat:8.5-jre8-alpine

ENV FCREPO_VERSION 4.8.0
ENV FCREPO_WEBAPP fcrepo-webapp-${FCREPO_VERSION}-SNAPSHOT.war

WORKDIR /etc/spring
COPY spring/* /etc/spring/

# Fcrepo webapp
COPY dist/${FCREPO_WEBAPP} ${CATALINA_HOME}/webapps/fcrepo.war
RUN echo "fcrepo.modeshape.configuration=classpath:/config/file-simple/repository.json" \
    >> ${CATALINA_HOME}/conf/catalina.properties \
 && echo "org.apache.catalina.webresources.Cache.level = SEVERE" \
    >> ${CATALINA_HOME}/conf/logging.properties



