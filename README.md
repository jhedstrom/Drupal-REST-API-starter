# REST API starter

A simple Drupal 8 install profile that highlights RESTful interactions with Drupal.

## Install

1. Install and initialize.
   ``` bash
   $> npm install
   $> grunt
   ```
1. Install the site. Change db url as needed
   ``` bash
   $> drush @restapi si --db-url=mysql://restapi:restapi@localhost/restapi -y
   ```
1. Create a user and give them admin (alternatively, configure permissions for another role)
   ``` bash
   $> drush ucrt --mail=example@example.com --password=pass mytestuser
   $> drush user-add-role administrator --name=mytestuser
   ```
1. Create content
   ``` bash
   $>  curl --include   --request POST   --user mytestuser:pass \
       --header 'Content-type: application/hal+json'   http://restapi.devl/entity/node \
       --data-binary '{"_links":{"type":{"href":"http://restapi.devl/rest/type/node/page"}}, "title":[{"value":"test title"}]}'
   ```
