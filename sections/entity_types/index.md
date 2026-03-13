+++
menus = 'entities'
title = 'Entity types form'
weight = 14
+++

# Entity types form

The entity types page lets you create new [content entity types and config entity
types](https://www.drupal.org/docs/drupal-apis/entity-api/entity-types).

## Content entity types

Content entity types are stored in the site's database, and are typically
created by site editors. They can have admin-created fields and revisions.
Nodes, taxonomy terms, media, and users are all content entity types.

1. In the Content entity types form section, click 'Add Content entity type'.
   This adds a form section for the entity type.
2. Enter the machine ID of the entity type. This autocompletes the entity type
   label and class name, but you can change these to something different.
3. Select as many of the Entity functionality options you want for your entity
   type:

   Fieldable
   : The entity type can have fields.

   Revisionable
   : The entities can have multiple revisions.

   Translatable
   : The entities can be translated.

   Changed
   : The entities have a timestamp field that stores their last change. The Entity class will implement EntityChangedInterface.

   Owner
   : The entities have a field that stores a user reference to their
     author. The Entity class will implement EntityOwnerInterface.

   Published
   : The entities have a status field indicating whether they are
     published or not. The Entity class will implement EntityPublishedInterface.




## Config entity types
