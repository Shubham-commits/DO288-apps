# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

# Exposing a non priviliged port
EXPOSE 8080

# Label to indicate changed port
LABEL io.openshift.expose-services="8080:http"

# Label to provide helpful metadata
LABEL io.k8s.description="A basic Apache HTTP Server child image, uses ONBUILD" \
      io.k8s.display-name="Apache HTTP Server" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="apache, httpd"

# Changing th eport number in the config file
RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf

# Change the group did and permissions of the folder
RUN chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd

# User instruction to use unprivileged user
USER 1001

