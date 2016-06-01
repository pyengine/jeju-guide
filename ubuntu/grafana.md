# Grafana

## Environment

Keyword     | Value                 | Description
----        | ----                  | ----
REPO        | https://packagecloud.io/grafana/stable/debian/| Grafana Repo for Debian

# Installation

Debian and Ubuntu users can install the latest stable version of Grafana using the apt-get package manager.

~~~bash
curl https://packagecloud.io/gpg.key | sudo apt-key add -
echo "deb ${REPO} wheezy main" | sudo tee /etc/apt/sources.list.d/grafana.list
~~~

And then to install and start the InfluxDB service

~~~bash
apt-get update
apt-get install -y adduser libfontconfig
apt-get install -y --force-yes grafana
~~~

## Start Grafana server

~~~bash
service grafana-server start
update-rc.d grafana-server defaults 95 10
~~~

* Reference
https://github.com/grafana/grafana/blob/master/docs/sources/installation/debian.md
