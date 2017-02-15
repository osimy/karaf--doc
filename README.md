FROM dockerfile/java
 +MAINTAINER osimy
 +ENV JAVA_HOME /usr/lib/jvm/jre
 +
 +RUN wget http://apache.openmirror.de/karaf/3.0.0/apache-karaf-3.0.0.tar.gz
 +RUN mkdir /opt/karaf
 +RUN tar --strip-components=1 -C /opt/karaf -xzvf apache-karaf-3.0.0.tar.gz
 +RUN rm apache-karaf-4.0.8.tar.gz
 +RUN mkdir /deploy
 +RUN sed -i 's/^\(felix\.fileinstall\.dir\s*=\s*\).*$/\1\/deploy/' /opt/karaf/etc/org.apache.felix.fileinstall-deploy.cfg
 +
 +VOLUME ["/deploy"]
 +EXPOSE 1099 8101 44444
 +ENTRYPOINT ["/opt/karaf/bin/karaf"]
