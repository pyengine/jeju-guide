# This is python virtual environment setttings

## Install PIP packages

~~~bash
pip install virtualenv
pip install virtualenvwrapper
mkdir ~/.virtualenvs
~~~

## Update ~/.bash_profile


~~~bash
echo "export WORKON_HOME=~/.virtualenvs" >> ~/.bash_profile
echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bash_profile
~~~

If you want to use now.

Reload .bash_profile, like


~~~bash
source ~/.bash_profile
~~~

# Usage

To create virutalenv, use mkvirtualenv <name> command

example
mkvirtualenv my_project


## Using requirements.txt

Each python project has requirements.txt
List all package version at requirements.txt
Then run, pip install -r requirements.txt
