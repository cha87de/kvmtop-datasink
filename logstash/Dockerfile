FROM docker.elastic.co/logstash/logstash:6.2.4
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD pipeline/ /usr/share/logstash/pipeline/
ADD config/ /usr/share/logstash/config/
RUN bin/logstash-plugin install --version 5.0.3 logstash-output-influxdb