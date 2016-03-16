# Jeju Guide book

This is repository for jeju guide book.
jeju automatically detect guide book from local disk to this repository.

# Example

If you want to install oracle JAVA using jeju.
Type following command in your host.

~~~bash
jeju -m oracle_java.md
~~~


jeju finds the guide book as following sequence.
* current local disk path : ./oracle_java.md
* Root Repository : https://raw.githubusercontent.com/pyengine/jeju-guide/oracle_java.md
* OS dependent Repository : https://raw.githubuserconent.com/pyengine/jeju-guide/centos/oracle_java.md
* OS version dependent Repository : https://raw.githubuserconent.com/pyengine/jeju-guide/centos/7.1/oracle_java.md

Otherwise, if you know collect url, specify full path

~~~bash
jeju -m https://raw.githubuserconent.com/pyengine/jeju-guide/centos/7.1/oracle_java.md
~~~

or

~~~bash
jeju -m centos/7.1/oracle_java.md
~~~
