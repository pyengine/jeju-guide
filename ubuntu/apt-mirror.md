# Ubuntu Apt mirror

Keyword     | Value         | Description
----        | ----          | ----
MIRROR_PATH | /var/www/apt-mirror   | local directory for saving mirror source
NUM_THREAD  | 10            | the number of threads

## Install Apt mirror package

Ubuntu apt-mirror is package of 'apt-mirror'

~~~bash
apt-get update
apt-get install -y apt-mirror
~~~

## Install Apache

Install apache and make directory for miror directory

~~~bash
apt-get install -y apache2
mkdir -p ${MIRROR_PATH}
~~~

# Configure apt-mirror

apt-mirror's configuration file is /etc/apt/mirror.list. There should already be a default configuration in it

edit /etc/apt/mirror.list

~~~text
############# config ##################
#
set base_path    ${MIRROR_PATH}
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     ${NUM_THREAD}
set _tilde 0
#
############# end config ##############

# Add remote source like
# deb http://ftp.daum.net/ubuntu trusty main restricted universe multiverse
~~~

# Running apt-mirror

run apt-mirror program
The command is 'apt-mirror'
