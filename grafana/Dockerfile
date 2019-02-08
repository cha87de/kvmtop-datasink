FROM rawmind/alpine-volume:0.0.2-2

VOLUME /var/lib/grafana/dashboards
VOLUME /etc/grafana/provisioning/dashboards
VOLUME /etc/grafana/provisioning/datasources
VOLUME /var/lib/grafana/plugins

ADD dashboards /var/lib/grafana/dashboards
ADD dashboards_config /etc/grafana/provisioning/dashboards
ADD datasources /etc/grafana/provisioning/datasources
ADD plugins /var/lib/grafana/plugins
