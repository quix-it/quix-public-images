FROM tomcat:8.5-jdk8

RUN apt-get update \
    && apt-get install -y --no-install-recommends dos2unix zip gettext less

# Remove default web applications
RUN rm -rf /usr/local/tomcat/webapps/ROOT/admin \
    && rm -rf /usr/local/tomcat/webapps.dist/ROOT/admin \
    && rm -f /usr/local/tomcat/conf/Catalina/localhost/manager.xml \
    && rm -f /usr/local/tomcat/conf/Catalina/localhost/host-manager.xml \
    && rm -f /usr/local/tomcat/conf/Catalina/localhost/admin.xml \
    && find webapps webapps.dist -maxdepth 1 -mindepth 1 -type d | grep -vE '/ROOT$' | xargs -r rm -rf

# Clean tomcat server info
RUN cd $(mktemp -d) \
    && mkdir -p org/apache/catalina/util \
    && echo "server.info=A" >org/apache/catalina/util/ServerInfo.properties \
    && echo "server.number=B" >>org/apache/catalina/util/ServerInfo.properties \
    && echo "server.built=C" >>org/apache/catalina/util/ServerInfo.properties \
    && zip -ur /usr/local/tomcat/lib/catalina.jar * \
    && cd - >/dev/null \
    && rm -rf $OLDPWD

# Turn off session façade recycling & Do not allow additional path delimiters"
RUN echo "JAVA_OPTS=\"\$JAVA_OPTS -Dorg.apache.catalina.connector.RECYCLE_FACADES=true\"" >>/usr/local/tomcat/bin/setenv.sh \
    && echo "JAVA_OPTS=\"\$JAVA_OPTS -Dorg.apache.catalina.connector.CoyoteAdapter.ALLOW_BACKSLASH=false\"" >>/usr/local/tomcat/bin/setenv.sh \
    && echo "JAVA_OPTS=\"\$JAVA_OPTS -Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=false\"" >>/usr/local/tomcat/bin/setenv.sh

RUN mkdir -p /usr/local/tomcat/conf/Catalina/localhost /usr/local/tomcat/conf/Catalina/templates /usr/local/tomcat/conf/custom_resources /usr/local/tomcat/conf/custom_contexts

# Modify default configuration
COPY files/server.xml files/context.xml files/logging.properties /usr/local/tomcat/conf/
COPY files/catalina.sh /usr/local/tomcat/bin/

RUN cd /usr/local/tomcat/lib && \
    curl -sL -O https://repo1.maven.org/maven2/org/postgresql/postgresql/42.2.21/postgresql-42.2.21.jar && \
    curl -sL -O https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.25/mysql-connector-java-8.0.25.jar

# Remove carriage returns from configuration files
RUN find "/usr/local/tomcat/conf" -type f -exec dos2unix -k {} \;

# Set up permissions for user `1001`
RUN useradd -d /usr/local/tomcat/ -M -u 1001 tomcat \
  && chown -R tomcat /usr/local/tomcat \
  && chmod -R "g+rwX" /usr/local/tomcat \
  && chmod -R "o-rw" /usr/local/tomcat

RUN apt-get purge -y --auto-remove \
    && rm -rf /var/lib/apt/lists/*;

USER 1001
