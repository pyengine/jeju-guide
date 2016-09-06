# About This document

This document is show how to install Oracle Java

# Environment

Keyword  | Value
-----    | -----
VERSION  | 8

# Installation

Current default version is Java8
If you want to install another version, change environment

~~~bash
apt-get install -y software-properties-common debconf-utils
~~~

# Expect is needed

~~~expect
spawn apt-add-repository ppa:webupd8team/java
expect "ctrl-c to cancel adding it"
send "\n";
interact
~~~


Install Oracle Java

~~~bash
apt-get update
echo "oracle-java${VERSION}-installer shared/accepted-oracle-license-v1-1 select true" | sudo debconf-set-selections
apt-get install -y oracle-java${VERSION}-installer
~~~

