FROM docker.elastic.co/logstash/logstash:6.2.4
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
RUN bin/logstash-plugin install --version 5.0.3 logstash-output-influxdb
RUN bin/logstash-plugin install logstash-filter-metricize
USER root
RUN yum install gettext -y
USER logstash
ADD pipeline/ /usr/share/logstash/pipeline-templates/
ADD config/ /usr/share/logstash/config/
ADD init/ /opt/docker-init/

ENV INPUT_PORT=12345
ENV OUTPUT_HOST=influxdb
ENV OUTPUT_PORT=8086
ENV OUTPUT_USER=
ENV OUTPUT_PASS=

ENTRYPOINT [ "/opt/docker-init/entrypoint" ]