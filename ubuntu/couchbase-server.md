# Install Couchbase Server Enterprise

## Environment

Keyword     |   Value           | Description
----        | ----              | ----
VER         | 4.1.0             | Server version
DOWNLOAD_SERVER | https://github.com/pyengine/packages/raw/master/deb  | Download from web (temporary)
ADMIN       | admin             | Admin account
PASSWORD    | my_password       | Password for admin
RAMSIZEMB   | 256               | Ram size
BUCKET_NAME | test_bucket       | Bucket name for new creation
BUCKET_RAMSIZE | 100            | Bucket ram size (MB)

# Installation

## Download package

Download package from server

~~~bash
wget ${DOWNLOAD_SERVER}/couchbase-server-enterprise_${VER}-ubuntu14.04_amd64.deb
dpkg -i couchbase-server-enterprise_${VER}-ubuntu14.04_amd64.deb
~~~

# Update configuration

## Cluster init

~~~bash
/opt/couchbase/bin/couchbase-cli cluster-init -c ${IP}:8091 --cluster-init-username=${ADMIN} \
    --cluster-init-password=${PASSWORD} \
   --cluster-init-ramsize=${RAMSIZEMB} \
   --services=data,index,query
~~~

## Check server status

~~~bash
/opt/couchbase/bin/couchbase-cli server-info -c ${IP}:8091 -u ${ADMIN} -p ${PASSWORD}
~~~

## Create new bucket

~~~bash
/opt/couchbase/bin/couchbase-cli bucket-create -c ${IP}:8091 -u ${ADMIN} -p ${PASSWORD} --bucket=${BUCKET_NAME} --bucket-ramsize=${BUCKET_RAMSIZE}
~~~
