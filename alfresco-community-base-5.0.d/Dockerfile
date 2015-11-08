FROM tomcat:7.0

# Definition of the data directory
RUN mkdir -p /srv/alfresco/alf_data
VOLUME /srv/alfresco/alf_data

# Tomcat settings
WORKDIR /usr/local/tomcat/
RUN mkdir shared shared/classes shared/lib
COPY tomcat .

EXPOSE 8080