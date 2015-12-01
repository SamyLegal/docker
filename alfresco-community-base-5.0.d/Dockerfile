FROM tomcat:7.0

# Download Alfresco
WORKDIR /tmp
ADD http://dl.alfresco.com/release/community/5.0.d-build-00002/alfresco-community-5.0.d.zip .
RUN unzip -e alfresco-community-5.0.d.zip
RUN	mv alfresco-community-5.0.d/web-server/webapps/alfresco.war /usr/local/tomcat/webapps
RUN	rm -rf /tmp/alfresco-community-5.0.d.zip

# Definition of the data directory
RUN mkdir -p /srv/alfresco/alf_data
VOLUME /srv/alfresco/alf_data

# Tomcat settings
WORKDIR /usr/local/tomcat/
COPY tomcat .

EXPOSE 8080