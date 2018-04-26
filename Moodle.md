== Create users in Drupal ==

== Create users in Moodle ==
To create users in Moodle, go to "Upload users"

First record contains the following:

`username, password, firstname, lastname, email`

Further rows should contain the data, separated by commas. Passwords should be random, 
since login will be via SAML

Passwords can be generated with:

apg -a 1 -m XX -n XX

== Enroll users in Moodle ==

