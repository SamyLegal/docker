FROM tomcat:7.0

# Download Alfresco
WORKDIR /tmp
#ADD http://dl.alfresco.com/release/community/5.0.d-build-00002/alfresco-community-5.0.d.zip .
ADD alfresco-community-5.0.d.zip .
RUN unzip -e alfresco-community-5.0.d.zip
RUN mv alfresco-community-5.0.d/web-server/webapps/alfresco.war /usr/local/tomcat/webapps
RUN rm -rf /tmp/alfresco-community-5.0.d.zip

# Definition of the data directory
RUN mkdir -p /srv/alfresco/alf_data
VOLUME /srv/alfresco

# Tomcat settings
WORKDIR /usr/local/tomcat/
COPY tomcat .

WORKDIR /srv/alfresco

# Port
EXPOSE 8080

# Environment variables
ENV ALFRESCO_HOME /srv/alfresco
ENV ALFRESCO_DB_USERNAME alfresco
ENV ALFRESCO_DB_PASSWORD alfresco
ENV ALFRESCO_DB_NAME alfresco
ENV ALFRESCO_DB_HOST localhost
ENV ALFRESCO_DB_PORT 3306
ENV ALFRESCO_DIR_ROOT /srv/alfresco/alf_data
