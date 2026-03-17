+++
menus = 'create'
title = 'Create a module'
weight = 2
+++

# Create a module

## New module

1. Go to Administration › Configuration › Development › Module Builder.

2. Click the 'Add module' button.

3. Enter the human-readable name for your module. The machine name is derived
   automatically, and you can choose to edit it, the same way as with any other
   config entity.

4. That's all you need to create the module entity. You can press the 'Save'
   button, or you can [enter further details]({{< relref "sections/info.md" >}}).

5. After you've saved the module, the form shows a number of tabs, each one for
   different types of modules components. You can navigate between these tabs in
   any order: each one is a form with its own save button.

6. When you've entered all your options, go to the 'Generate' tab to see the
   module code and write the files.

## Adopt a module

Instead of creating a new module from scratch, you can adopt an existing module.
This allows you to add to existing code.

1. Go to Administration › Configuration › Development › Module Builder.

2. Click the 'Adopt existing module' button.

3. Select one of the modules in the list.

4. Either:
   - Click 'Adopt module' to create a new module config entity using the name of
     the selected module. This takes you to the Info tab for the new module
     where you can start entering data for it.
   - Click 'Adopt module and adopt components' to create a new module config
     entity and go to the Adopt tab, where you can adopt individual components
     of the module on disk.
