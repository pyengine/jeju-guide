# Building VoltDB

# Setting up your environment

Keyword         | Value | Description
----            | ----  | ----
INSTALL_JAVA    | True  | Install Oracle Java 8 (True|False)

## Prerequisite

Install Oracle Java 8

~~~bash
if [ ${INSTALL_JAVA} == 'True' ]
    then
        echo "### Install Oracle Java ####"
        jeju -m oracle-java.md
    else
        echo "### Does not install Oracle Java ###"
fi
~~~

Install dependencies as packages

~~~bash
apt-get -y install ant build-essential ant-optional python cmake \
    valgrind ntp ccache git-arch git-completion git-core git-svn git-doc \
    git-email python-httplib2 python-setuptools python-dev apt-show-versions
~~~

# Getting the code

Clone the source

~~~bash
git clone https://github.com/VoltDB/voltdb.git
~~~

## Building

~~~bash
cd voltdb
ant
~~~

To do a clean build, run ant clean. It's a good idea to do a clean build.

# Start

To start voltdb, disable THP (Transparent Huge Page)

~~~bash
echo "never" > /sys/kernel/mm/transparent_hugepage/enabled
echo "never" > /sys/kernel/mm/transparent_hugepage/enabled
~~~

To start voltdb instance

./bin/voltdb create
