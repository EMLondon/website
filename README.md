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
