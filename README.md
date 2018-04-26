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

`echo -n <password><salt> | md5sum`

So, if the password is `Vurcyied` and the salt is `Ibzocmash`, do:

`echo -n VurcyiedIbzocmash | md5sum`

Then insert like this:

INSERT INTO `jem5_users` (`id`, `name`, `username`, `email`, `password`, `params`) VALUES (NULL, 'Test User', 'tuser', 'test.user@example.com', 'b43ddc9ff084753b0f502e6f0fcce976:Ibzocmash', '');

* Add user to usergroups: 

For consultants: 
INSERT INTO `eml`.`jem5_user_usergroup_map` (`user_id`, `group_id`) VALUES ('<user_id>', '11');
INSERT INTO `eml`.`jem5_user_usergroup_map` (`user_id`, `group_id`) VALUES ('<user_id>', '32');

For admin staff:
INSERT INTO `eml`.`jem5_user_usergroup_map` (`user_id`, `group_id`) VALUES ('<user_id>', '16');

* Add user to `jem5_comprofiler`

INSERT INTO `eml`.`jem5_comprofiler` (`id`, `user_id`, `firstname`, `lastname`, `cb_displayname`) VALUES ('<user_id>', '<user_id>', '<first>', '<last>', '<display_name>');

You can make most of this happen with this extension:

http://extensions.openoffice.org/en/project/cryptographic-hash-functions-uno-component-openofficeorg#sthash.42nVdsJE.dpuf

==Forums==
* Create user:

```
cd /discourse
sudo ./launcher enter app
rails c
u = User.create!(username: "name", email: "name@email.com", password: "password")
u.activate
```

* Add user to appropriate category


