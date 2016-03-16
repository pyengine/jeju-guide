# Install nGrinder controller

## Envirionment

Keyword     |   Value       | Description
----        |   ----        | ----
VER         | 3.3           | nGrinder version
TARGET      | /opt/nGrinder | nGrinder directory to install

## Download package

Download nGrinder from sourceforge

~~~bash
mkdir -p ${TARGET}
wget -O ${TARGET}/ngrinder-controller-${VER}.war http://downloads.sourceforge.net/project/ngrinder/ngrinder-3.3/ngrinder-controller-3.3.war?r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fngrinder%2Ffiles%2Fngrinder-3.3%2Fngrinder-controller-3.3.war%2Fdownload&ts=1455587749&use_mirror=jaist
~~~

## Update ngrinder script

edit /usr/local/bin/ngrinder-start.sh

~~~text
nohup /usr/bin/java -XX:MaxPermSize=200m -jar ${TARGET}/ngrinder-controller-${VER}.war &
~~~

## Update ngrinder stop script

edit /usr/local/bin/ngrinder-stop.sh

~~~text
pid=`ps aux | grep ngrinder-controller | awk '{print $2}'`
kill -9 $pid
~~~

## Update permission

~~~bash
chmod 755 /usr/local/bin/ngrinder-start.sh
chmod 755 /usr/local/bin/ngrinder-stop.sh
~~~

## Update start-script with service

edit /etc/init.d/ngrinder

~~~text
#!/bin/bash
# nGrinder start,stop shell
#
# description: bla bla

case $1 in
    start)
        /bin/bash /usr/local/bin/ngrinder-start.sh
    ;;
    stop)
        /bin/bash /usr/local/bin/ngrinder-stop.sh
    ;;
    restart)
        /bin/bash /usr/local/bin/ngrinder-stop.sh
        /bin/bash /usr/local/bin/ngrinder-start.sh
    ;;
esac
exit 0
~~~

## Update permission

~~~bash
chmod 755 /etc/init.d/ngrinder
~~~
