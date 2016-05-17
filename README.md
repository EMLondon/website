# Systems used in the site:
* Drupal
* Discourse
* Mattermost
* Moodle

# Special additions
* OAuth2 Basic (Discourse)
* OAuth2 loginprovider (Drupal)
* Plus addressing (Dovecot):
```
dovecot   unix  -       n       n       -       -       pipe
   flags=DRhu user=vmail:vmail argv=/usr/lib/dovecot/dovecot-lda -f ${sender} -d ${user}@${nexthop}
```
* Plus addressing ([Postfix](http://www.stevejenkins.com/blog/2011/03/how-to-use-address-tagging-usertagexample-com-with-postfix/): recipient_delimiter = +))

# Creating a new user
There are several systems that are needed to fully activate an account, though hopefully this should reduce with time.

1. Drupal: Add user and add them to the proper groups
2. Kitab:
* Add user to jem5_users table
* For password, do: 
* Add usergroups: 11, 32
3. Forums:
* Add user to appropriate category


