# Pyengine

## Prerequisite

Keyword | Value     | Description
----    | ----      | ----
PROJECT | myproject | Project name
 
# Installation

## Install libraries

Pyengine is based on apache and python django framework

~~~bash
apt-get update
export DEBIAN_FRONTEND=noninteractive
apt-get install -y git python-dev python-pip mariadb-server apache2 libapache2-mod-wsgi python-mysqldb libyaml-cpp-dev libyaml-dev
~~~

## Install PIP libraries for django

~~~bash
pip install django
pip install django-log-request-id
pip install dicttoxml
pip install xmltodict
pip install routes
pip install rsa
pip install pytz
pip install pyyaml
pip install django-cors-headers
~~~

## Download source

Download pyengine source

~~~bash
cd /opt/
git clone https://github.com/pyengine/pyengine.git ${PROJECT}
~~~

## Update python module path environment

edit /usr/local/lib/python2.7/site-packages/pyengine.pth

~~~text
/opt/${PROJECT}
~~~

# Update Configuration

## Update Apache configuration

edit /etc/apache2/sites-available/pyengine.conf

~~~text
<VirtualHost *:80>
    Alias /static    /opt/${PROJECT}/static
    <Directory /opt/${PROJECT}/static>
        Require all granted
    </Directory>

    WSGIScriptAlias / /opt/${PROJECT}/pyengine/wsgi.py
    WSGIPassAuthorization On

    <Directory /opt/${PROJECT}/pyengine>
    <Files wsgi.py>
        Require all granted
    </Files>
    </Directory>

    AddDefaultCharset UTF-8
</VirtualHost>
~~~

Enable the pyengine

~~~bash
a2ensite pyengine
~~~

# Create Database

Create pyengine database

~~~expect
spawn mysql -u root -e "create database pyengine character set utf8 collate utf8_general_ci"
expect "Enter password: "
send "\n";
interact
~~~

## Update django DB

~~~bash
mkdir /var/log/pyengine
chown -R www-data:www-data /var/log/pyengine

cd /opt/${PROJECT}
python manage.py makemigrations
python manage.py migrate
~~~

# Restart Apache

~~~bash
service apache2 restart
~~~
