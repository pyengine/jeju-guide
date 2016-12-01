# Install Telegraf + Remote Sending

## Environment

Keyword     |       Value           | Description
----        | ----                  | ----
INFLUXDB      | 127.0.0.1             | Remote DB like Influx DB
PORT        | 8086                  | Influx DB UDP Port
PKG         | telegraf_1.1.1_amd64.deb | Telegraf package
REPO        | https://dl.influxdata.com/telegraf/releases | Telegraf download url
DATABASE    | mydatabase            | name of Influxdb Database

# Install Telegraf

~~~bash
wget ${REPO}/${PKG}
dpkg -i ${PKG}
~~~

## Update Configuration

backup default config file

~~~bash
cp /etc/telegraf/telegraf.conf /etc/telegraf/telegraf.conf.org
~~~

edit /etc/telegraf/telegraf.conf

~~~text
[global_tags]


[agent]
  interval = "10s"
  round_interval = true

  metric_batch_size = 1000
  metric_buffer_limit = 10000

  collection_jitter = "0s"

  flush_interval = "10s"
  flush_jitter = "0s"

  debug = false
  quiet = false
  hostname = ""
  omit_hostname = false


###############################################################################
#                            OUTPUT PLUGINS                                   #
###############################################################################

[[outputs.influxdb]]
  urls = ["http://${INFLUXDB}:${PORT}"] # required
  database = "${DATABASE}" # required
  precision = "s"

  retention_policy = "autogen"
  write_consistency = "any"

  timeout = "5s"


###############################################################################
#                            INPUT PLUGINS                                    #
###############################################################################

[[inputs.cpu]]
  percpu = false
  totalcpu = true
  fielddrop = ["time_*"]


[[inputs.disk]]
  ignore_fs = ["tmpfs", "devtmpfs"]


[[inputs.diskio]]

[[inputs.kernel]]


[[inputs.mem]]


[[inputs.processes]]


[[inputs.swap]]


[[inputs.system]]

~~~

# Restart service

~~~bash
service telegraf restart
~~~
