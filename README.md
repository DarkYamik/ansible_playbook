In order to use this example, you must create a vagrant VM called ubuntu1804.

For testing purposes it only allows this host

This example uses a jinja template to generate the index.html file. Some of the variables are taken from plain text variables and one of them called "this_secret_text" is taken from a vault. In order to decrypt it, the password is 1234.