--------------
Frontend-Containers

In order to use this example, you must create a vagrant VM called ubuntu1804.

For testing purposes it only allows this host

This example uses a jinja template to generate the index.html file. Some of the variables are taken from plain text variables and one of them called "this_secret_text" is taken from a vault. In order to decrypt it, the password is 1234.

It also modifies the listening port of apache by using a Regex expression to find and modify the ports.conf file

--------------

Mysql In order to run this, you need to deploy mysqlmaster and mysqlslave vagrant machines

It will download and install podman, create mysql containers and then create a master-slave replication automatically.

For now the passwords are in clear text but it has to be modified to use vault variables


--------
podman

Installs podman on the target machines