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

edit /usr/local/bin/ngrinder.sh

~~~text
/usr/bin/java -XX:MaxPermSize=200m -jar ${TARGET}/ngrinder-controller-${VER}.war
~~~

## Update permission

~~~bash
chmod 755 /usr/local/bin/ngrinder.sh
~~~

## Update start-script with systemd

edit /usr/lib/systemd/system/ngrinder.service

~~~text
[Unit]
Description=nGrinder controller

[Service]
Type=simple
ExecStart=/usr/local/bin/ngrinder.sh

[Install]
WantedBy=multi-user.target
~~~
