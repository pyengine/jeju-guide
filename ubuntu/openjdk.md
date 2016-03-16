# Install OpenJDK

## Environment

Keyword | Value     | Description
----    |   ----    | ----
VER     | 7     | Possible value is 6 or 7 or 8

## Installation

~~~bash
apt-get -y install openjdk-${VER}-jdk
~~~

## Update JAVA_HOME

edit /etc/profile.d/java.sh

~~~text
export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64/
~~~

