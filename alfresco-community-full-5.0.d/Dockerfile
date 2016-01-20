FROM tomcat:7.0

# APR - Tomcat native library - http://tomcat.apache.org/native-doc/
# Tomcat native library we have better performance and metrics for the server
RUN apt-get update && apt-get install -y libapr1-dev libssl-dev

# Alfresco
RUN mkdir -p /srv/alfresco /srv/alfresco/alf_data /srv/alfresco/amps_share
WORKDIR /srv/alfresco
COPY alfresco .
VOLUME /srv/alfresco/alf_data
RUN ln -s /usr/local/tomcat /srv/alfresco/tomcat

# Tomcat settings
WORKDIR /usr/local/tomcat/
RUN mkdir shared shared/classes shared/lib
COPY tomcat .

# Sharepoint
WORKDIR /srv/alfresco

# Génération de la clé privé/public du repository dans le keystore
RUN keytool -genkey -alias alfresco -keystore keystore/alfresco-keystore.jks -storepass alfresco -keypass alfresco -keyalg RSA -validity 360 -keysize 2048 -storetype JKS -dname "CN=localhost, OU=Development, O=Alfresco, L=Vannes, ST=Brittany, C=FR"

# Génération et export du certificat dans un fichier
RUN keytool -exportcert -alias alfresco -file keystore/alfresco.cer -keystore keystore/alfresco-keystore.jks -storepass alfresco -storetype JKS

# Import du certificat dans le trustore par défaut de JAVA
RUN keytool -importcert -alias alfresco -file keystore/alfresco.cer -keypass alfresco -noprompt -trustcacerts -storetype JKS -keystore /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/security/cacerts -storepass changeit

RUN chmod +x ./bin/apply_amps.sh
RUN ./bin/apply_amps.sh

EXPOSE 8080
EXPOSE 7070
EXPOSE 443
