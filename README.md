# kvmtop-datasink

Datasink for kvmtop: kvmtop send monitoring data to logstash, which stores them into influxdb. A chronograf or grafana dashboard visualises the kvmtop data stored in influxdb.

```
                                      kvmtop-datasink
                  +-----------------------------------------------------+
                  |                                                     |
+------------     | +------------+     +------------+     +-----------+ |
|           |     | |            |     |            |     |           | |
|  kvmtop   +---> | |  logstash  +---> |  influxdb  +---> |  grafana  | |
|           |     | |            |     |            |     |           | |
+------------     | +------------+     +------------+     +-----------+ |
                  |                                                     |
                  +-----------------------------------------------------+
```

## Deploy with Docker Compose

On a host wich Docker and Docker Compose, checkout this repository, open a terminal inside your git clone and then run

```
docker-compose up -d
```

Make sure to change the password for the influxdb in the `docker-compose.yml` file. If you do so, you need to change it in `logstash/pipeline/kvmtop2influxdb.conf` as well, and rebuild the logstash container image by yourself.

Then on a kvm enabled host, start [kvmtop](https://github.com/cha87de/kvmtop) and send the output to your logstash instance, e.g.

```
kvmtop --cpu --printer=json --output=tcp --target=127.0.0.1:12345
```

Hint: [Installation of kvmtop](https://github.com/cha87de/kvmtop/releases)
