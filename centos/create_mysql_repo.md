# Create MySQL Cluster Repo

This is working for MySQL Cluster 7.5.
Version 7.4 has different files. (not working)

## Environment

Keyword         | Value             | Description
----            | ----              | ----
VER             | 7.5.5-1           | MySQL Cluster Version
ARCH            | x86_64            | Architecture (x86_64 | i686)
OS              | 6                 | RedHat Version (5 | 6 | 7)
TARGET          | /tmp/repo         | Local Repositoy


To make local repo, createrepo package is needed

~~~bash
yum install -y createrepo
~~~

# Download Package

~~~bash
BASE=https://dev.mysql.com/get/Downloads/MySQL-Cluster-7.5/
PROD=mysql-cluster-community
VER=${VER}
OS=${OS}
ARCH=${ARCH}
TARGET=${TARGET}

CLIENT=$PROD-client-$VER.el$OS.$ARCH.rpm
COMMON=$PROD-common-$VER.el$OS.$ARCH.rpm
DATA=$PROD-data-node-$VER.el$OS.$ARCH.rpm
LIBS1=$PROD-libs-$VER.el$OS.$ARCH.rpm
LIBS2=$PROD-libs-compat-$VER.el$OS.$ARCH.rpm
MGMT=$PROD-management-server-$VER.el$OS.$ARCH.rpm

mkdir -p $TARGET
wget -O $TARGET/$CLIENT $BASE/$CLIENT
wget -O $TARGET/$COMMON $BASE/$COMMON
wget -O $TARGET/$DATA $BASE/$DATA
wget -O $TARGET/$LIBS1 $BASE/$LIBS1
wget -O $TARGET/$LIBS2 $BASE/$LIBS2
wget -O $TARGET/$MGMT $BASE/$MGMT
~~~

# Create Repo file

Create metadata

~~~bash
createrepo ${TARGET}
~~~

edit /etc/yum.repos.d/mysql.repo

~~~text
[mysql]
name=MySQL Cluster
baseurl=file://${TARGET}
enabled=1
gpgcheck=0
~~~
