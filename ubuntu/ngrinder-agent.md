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
wget -O agent.tar http://${CONTROLLER}/agent/download
tar xvf agent.tar
~~~

# Update start script

edit /etc/init.d/ngrinder-agent

~~~text
#!/bin/bash
# nGrinder agent
#
# description: ngrinder agent

case $1 in
    start)
        nohup /opt/ngrinder-agent/run_agent.sh &
    ;;
    stop)
        /opt/ngrinder-agent/stop_agent.sh
    ;;
    restart)
        /opt/ngrinder-agent/stop_agent.sh
        nohup /opt/ngrinder-agent/run_agent.sh &
    ;;
esac
exit 0
~~~

## Permit script

~~~bash
chmod 755 /etc/init.d/ngrinder-agent
~~~
