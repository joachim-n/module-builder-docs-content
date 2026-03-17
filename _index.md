+++
menus = 'main'
title = 'Home'
+++

# Module Builder

Module Builder is a Drupal module which creates code for Drupal modules. Module
Builder provides an interface in your Drupal site's admin area, which guides you
through a series of forms to set the components for your module and their
options, and then write the code files. You can write a new module from scratch,
or add components to an existing module.

The options for your module are stored in Drupal configuration, as a [config
entity](https://www.drupal.org/docs/drupal-apis/entity-api/configuration-entity),
so you can return to your module's options and add or change things, and then
re-generate the updated parts of the code.

Module Builder is *analytical*: it analyses your codebase to discover what different components are
available to build. For example, it will offer hooks and plugins based on the
hooks and plugin types that are found in your site's code.

Module Builder is *adaptive*: the forms that show options for the module are
dynamically generated from a schema defined in the [Drupal Code Builder
library](https://github.com/drupal-code-builder/drupal-code-builder). New
releases of Drupal Code Builder will often cause Module Builder to show new
options in its forms.

## Coding standards

Module Builder's code generating library has an extensive suite of tests, which
verify that all generated code complies to Drupal Coding Standards.