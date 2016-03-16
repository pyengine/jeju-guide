# Install OpenJDK

## Environment

Keyword | Value     | Description
----    |   ----    | ----
VER     | 1.7.0     | Possible value is 1.6.0 or 1.7.0 or 1.8.0

## Installation

~~~bash
yum -y install java-${VER}-openjdk
~~~

## Update JAVA_HOME

edit /etc/profile.d/java.sh

~~~text
export JAVA_HOME=/usr/lib/jvm/jre
~~~

