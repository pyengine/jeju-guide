# nGrinder agent installation

## Environment

Keyword     |   Value               | Description
----        |   ----                | ----
CONTROLLER  | 192.168.1.1:8080      | nGrinder controller address

## Prerequisite

JAVA and JAVA_HOME must be set

~~~bash
which java
echo $JAVA_HOME
echo "Is it correct?"
~~~

## Download & Install agent 

Download agent package from nGrinder controller

~~~bash
cd /opt
wget -o agent.tar http://${CONTROLLER}/agent/download
tar xvf agent.tar
~~~

# Update start script

edit /usr/lib/systemd/system/ngrinder-agent.service

~~~text
[Unit]
Description=nGrinder agent

[Service]
Type=simple
ExecStart=/opt/ngrinder-agent/run_agent.sh

[Install]
WantedBy=multi-user.target
~~~

## Re-start service

~~~bash
systemctl daemon-reload
systemctl start ngrinder-agent.service
~~~

