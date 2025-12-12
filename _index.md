+++
menus = 'main'
title = 'Home'
+++

# Overview

Module Builder is a Drupal module which creates code for Drupal modules. Module Builder provides an interface
in your Drupal site's admin area, which guides you through a series of forms to set the components for your module and their options, and then write the code files. You can write a new module from scratch, or add components to an existing module.

The options for your module are stored in Drupal configuration, as a config entity, so you can return to your module's options and add or change things, and then re-generate the updated parts of the code.

Module Builder analyses your codebase to discover what different components are available to build. For example, it will offer hooks and plugins based on the hooks and plugin types that are found in your site's code.

# Installation

1. Install Module Builder using Composer, the same as any other Drupal module.

2. Enable the module in the UI or with Drush.

3. Go to Administration › Configuration › Development › Module Builder › Analyse
   code.

4. Click the 'Update code analysis' button.

You should run the code analysis again each time you enable new modules, update
modules, or add code to your custom modules, so that Module Builder knows about
new components in your codebase.

# Create a module

1. Go to Administration › Configuration › Development › Module Builder.

2. Click the 'Add module' button.

3. Enter the human-readable name for your module. The machine name is derived
   automatically, and you can choose to edit it, the same way as with any other
   config entity.

4. That's all you need to create the module entity. You can press the Save
   button, or you can enter further details.

5. Once you've saved the module, the form shows a number of tabs, each one for
   different types of modules components. You can navigate between these tabs in
   any order: each one is a form with its own save button.

6. When you've entered all your options, go to the Generate tab to see the module code and write the files.

# Module options in detail

## Info

The Info tab is the form initially used to create the module. It holds data that goes in the module's `info.yml` file.

It also allows you to specify where the module will be written. By default, modules are written to `modules/custom`, but you can specify that the module is a submodule inside another one, or a test module in another module's test code.

For more information on the info properties, see [the info file documentation](https://www.drupal.org/docs/develop/creating-modules/let-drupal-know-about-your-module-with-an-infoyml-file).

## Hooks

The Hooks tab lets you add hook implementations. These can be
procedural functions, or use the new OO-style hooks which are methods in a
class.

### Object-oriented hooks

Object-oriented hooks are methods in a PHP class. These were [introduced in
Drupal 11.1](https://www.drupal.org/blog/drupal-11-1-0), and can be
backwards-compatible with older versions of Drupal.

1. Click the 'Add a Hook classes item' button. This adds a new section to the
   form for the hooks class. This shows:
   - The hooks class name.
   - A table of hooks implementations.
   - The injected services.
2. The bottom (and currently only) row of the hook implementations table shows
   a search box for the hook name. Start typing part of the hook name to filter
   the autocomplete dropdown. You can click on the documentation link for a hook
   to read more about it on the Drupal API site.
3. Click on the hook in the dropdown, then click the
   'Add hook method' button. This adds your hook to the table.
4. If your hook uses token replacements in its name (such as
   `hook_form_FORM_ID_alter`, or `hook_ENTITY_TYPE_access`), its table row will
   show a text box for the value. So for example, if you want to implement
   `hook_node_access`, enter 'node'.
5. You can add as many hooks methods as you want.
6. You can add services to inject into the hooks class. The 'Injected
   services' form element has an autocomplete.
7. You can add as many hook classes as you like.

### Procedural hooks

Procedural hooks are functions in plain PHP file, often the `.module` file.

Some hooks cannot be OO, and must be implemented as procedural. For these, use
the hook groups section of the form.

1. In the 'Hook implementation type' radios element, select 'Functions in
   procedural files'.
2. Start typing the hook name in the filter below.
3. Select the hook's checkbox.

## Plugins

The Plugins tab lets you add plugins and plugin types.

### Plugins

The plugins section of the form lets you add plugins.

1. In the Plugin type form element, start typing part of the plugin type name to
   filter the autocomplete dropdown. You can click on the documentation link for
   a plugin type to read more about it on the Drupal API site.
2. Click 'Add a plugins item'. This adds a form section for the plugin.
3. Enter the plugin ID.
4. The rest of the form differs depending on the type of the plugin.

#### Attribute or annotation-based plugins

These are plugins which are a class with an attribute or annotation to declare it to the plugin system.

All the form elements after the plugin ID are optional.

1. The class name form element will fill in automatically based on the plugin ID you enter.
   You can rewrite this if you want.
2. You can add services to inject into the plugin class. The 'Injected
   services' form element has an autocomplete.
3. You can set the plugin to use a deriver. This adds a deriver class which
   dynamically defines multiple plugins based on the plugin class.
4. You can specify another plugin whose class will be used as the parent of your class.

You can have your plugin class replace the class of an existing plugin, instead
of being a new plugin. To do this:

1. Specify the plugin to replace as the 'Parent class plugin ID'
2. Enable the 'Replace parent plugin' checkbox.

#### YAML plugins

These are plugins which are defined in a YAML file.

All the form elements after the plugin ID are optional.

1. You can set the plugin to use a deriver. This adds a deriver class which
   dynamically defines multiple plugins based on the plugin.
2. You can specify to add a custom class for your plugin. YAML plugins typically
   all use a single class, unless a different one is specified in the plugin
   definition.
3. If using a custom plugin class, you can add services to inject into it. The 'Injected
   services' form element has an autocomplete.

### Plugin types

The plugin types section of the form lets you add plugin types.

This will generate several code files, including:

- A base class for the plugin type's plugins.
- An interface for the plugin type's plugins.
- A plugin manager service class.
- An api.php file documenting the plugin type alter hook.

1. Select the plugin discovery type. This can be one of:
  - Attribute-based plugins: Each plugin is a class with an attribute to declare the plugin data.
  - Annotation-based plugins: Each plugin is a class with an annotation to declare the plugin data.
  - YAML-based plugins: Plugins are declared in a single YAML file, and usually share a single class.
2. Click 'Add a plugin types item'. This adds a form section for the plugin type.
3. Enter the plugin type ID. This will be used to form the service ID of the plugin manager service.
4. Subsequent form elements for the label, class name, subdirectory, and so on are filled in automatically for you. You can rewrite these if you want.
5. For an attribute or annotation plugin, you can add properties in addition to the ID, label, and description
   which are automatically included.
6. You can add services to inject into the plugin base class. The 'Injected
   services' form element has an autocomplete.

Once you have generated the code files for your plugin type, you can enable the module, re-do code analysis,
and then Module Builder will be able to generate plugins of this new type.
