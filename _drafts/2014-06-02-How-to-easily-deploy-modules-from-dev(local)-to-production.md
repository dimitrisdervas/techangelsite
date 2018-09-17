---
title: How to easily tranfer only enabled modules from dev-local to production-server
date: 2014-06-02 00:00:00 +0000
categories:
- blog
layout: blogpost

---
After a lot of years I finally found an easy way for me to move only the enabled modules from my local dev environment to my productio server

I wanted my modules to be exactly the same version
I also wanted to be just the main project not all the submodules a project contains
Needed Module:

[Enabled Modules](https://drupal.org/project/enabled_modules)

Dependencies:
[Views](http://drupal.org/project/views)
[Views system](http://drupal.org/project/views_system)

this module basicaly create a view that let us see all of our modules nad filter them

But I wanted a simple list with all the modules that I would use with Drush dl

So I installed two more modules
For a small number of modules 30?

[Views Delimiter list](https://drupal.org/project/views_delimited_list)

For a larger number of modules
[Views Data source](https://drupal.org/project/views_datasource)

And the view I created - it overrides the view of the module
    $view = new view();
    $view->name = 'enabled_modules';
    $view->description = '';
    $view->tag = 'default';
    $view->base_table = 'system';
    $view->human_name = 'Enabled Modules';
    $view->core = 7;
    $view->api_version = '3.0';
    $view->disabled = FALSE; /* Edit this to true to make a default view disabled initially */

    /* Display: Master */
    $handler = $view->new_display('default', 'Master', 'default');
    $handler->display->display_options['title'] = 'Enabled Modules CSV';
    $handler->display->display_options['use_more_always'] = FALSE;
    $handler->display->display_options['access']['type'] = 'perm';
    $handler->display->display_options['access']['perm'] = 'view enabled modules';
    $handler->display->display_options['cache']['type'] = 'none';
    $handler->display->display_options['query']['type'] = 'views_query';
    $handler->display->display_options['query']['options']['query_comment'] = FALSE;
    $handler->display->display_options['exposed_form']['type'] = 'basic';
    $handler->display->display_options['pager']['type'] = 'none';
    $handler->display->display_options['pager']['options']['offset'] = '0';
    $handler->display->display_options['style_plugin'] = 'grid';
    $handler->display->display_options['style_options']['grouping'] = 'info_project';
    $handler->display->display_options['style_options']['columns'] = '3';
    $handler->display->display_options['style_options']['fill_single_line'] = FALSE;
    $handler->display->display_options['row_plugin'] = 'fields';
    /* Field: System: Display name */
    $handler->display->display_options['fields']['info_name']['id'] = 'info_name';
    $handler->display->display_options['fields']['info_name']['table'] = 'system';
    $handler->display->display_options['fields']['info_name']['field'] = 'info_name';
    $handler->display->display_options['fields']['info_name']['exclude'] = TRUE;
    $handler->display->display_options['fields']['info_name']['hide_alter_empty'] = FALSE;
    /* Field: System: Name */
    $handler->display->display_options['fields']['name']['id'] = 'name';
    $handler->display->display_options['fields']['name']['table'] = 'system';
    $handler->display->display_options['fields']['name']['field'] = 'name';
    $handler->display->display_options['fields']['name']['label'] = '';
    $handler->display->display_options['fields']['name']['alter']['alter_text'] = TRUE;
    $handler->display->display_options['fields']['name']['alter']['text'] = '[info_name] ([name])';
    $handler->display->display_options['fields']['name']['element_label_colon'] = FALSE;
    $handler->display->display_options['fields']['name']['hide_alter_empty'] = FALSE;
    /* Field: System: Project */
    $handler->display->display_options['fields']['info_project']['id'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['table'] = 'system';
    $handler->display->display_options['fields']['info_project']['field'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['exclude'] = TRUE;
    $handler->display->display_options['fields']['info_project']['alter']['path'] = 'http://drupal.org/[info_project]';
    $handler->display->display_options['fields']['info_project']['alter']['external'] = TRUE;
    $handler->display->display_options['fields']['info_project']['hide_alter_empty'] = FALSE;
    $handler->display->display_options['fields']['info_project']['system_info_project_link'] = 1;
    /* Filter criterion: System: Type */
    $handler->display->display_options['filters']['type']['id'] = 'type';
    $handler->display->display_options['filters']['type']['table'] = 'system';
    $handler->display->display_options['filters']['type']['field'] = 'type';
    $handler->display->display_options['filters']['type']['value'] = array(
      'module' => 'module',
    );
    /* Filter criterion: System: Status */
    $handler->display->display_options['filters']['status']['id'] = 'status';
    $handler->display->display_options['filters']['status']['table'] = 'system';
    $handler->display->display_options['filters']['status']['field'] = 'status';
    $handler->display->display_options['filters']['status']['value'] = '1';

    /* Display: Enabled Modules */
    $handler = $view->new_display('page', 'Enabled Modules', 'page');
    $handler->display->display_options['defaults']['title'] = FALSE;
    $handler->display->display_options['title'] = 'Enabled Modules';
    $handler->display->display_options['path'] = 'enabled-modules';
    $handler->display->display_options['menu']['type'] = 'normal';
    $handler->display->display_options['menu']['title'] = 'Enabled Modules';
    $handler->display->display_options['menu']['weight'] = '0';

    /* Display: Delimited list */
    $handler = $view->new_display('page', 'Delimited list', 'page_1');
    $handler->display->display_options['defaults']['title'] = FALSE;
    $handler->display->display_options['title'] = 'Enabled Modules LIst';
    $handler->display->display_options['defaults']['group_by'] = FALSE;
    $handler->display->display_options['defaults']['query'] = FALSE;
    $handler->display->display_options['query']['type'] = 'views_query';
    $handler->display->display_options['query']['options']['pure_distinct'] = TRUE;
    $handler->display->display_options['defaults']['style_plugin'] = FALSE;
    $handler->display->display_options['style_plugin'] = 'views_delimited_list';
    $handler->display->display_options['style_options']['long_count'] = '3';
    $handler->display->display_options['style_options']['separator_two'] = 'delimiter';
    $handler->display->display_options['style_options']['separator_long'] = 'conjunctive';
    $handler->display->display_options['style_options']['prefix'] = 'prefix';
    $handler->display->display_options['defaults']['style_options'] = FALSE;
    $handler->display->display_options['defaults']['row_plugin'] = FALSE;
    $handler->display->display_options['row_plugin'] = 'fields';
    $handler->display->display_options['row_options']['inline'] = array(
      'info_project' => 'info_project',
      'info' => 'info',
    );
    $handler->display->display_options['row_options']['separator'] = '-';
    $handler->display->display_options['defaults']['row_options'] = FALSE;
    $handler->display->display_options['defaults']['fields'] = FALSE;
    /* Field: System: Project */
    $handler->display->display_options['fields']['info_project']['id'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['table'] = 'system';
    $handler->display->display_options['fields']['info_project']['field'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['label'] = '';
    $handler->display->display_options['fields']['info_project']['alter']['path'] = 'http://drupal.org/[info_project]';
    $handler->display->display_options['fields']['info_project']['alter']['external'] = TRUE;
    $handler->display->display_options['fields']['info_project']['element_label_colon'] = FALSE;
    $handler->display->display_options['fields']['info_project']['hide_alter_empty'] = FALSE;
    $handler->display->display_options['fields']['info_project']['system_info_project_link'] = 0;
    /* Field: System: Display name */
    $handler->display->display_options['fields']['info_name']['id'] = 'info_name';
    $handler->display->display_options['fields']['info_name']['table'] = 'system';
    $handler->display->display_options['fields']['info_name']['field'] = 'info_name';
    $handler->display->display_options['fields']['info_name']['label'] = '';
    $handler->display->display_options['fields']['info_name']['exclude'] = TRUE;
    $handler->display->display_options['fields']['info_name']['element_label_colon'] = FALSE;
    /* Field: System: Info */
    $handler->display->display_options['fields']['info']['id'] = 'info';
    $handler->display->display_options['fields']['info']['table'] = 'system';
    $handler->display->display_options['fields']['info']['field'] = 'info';
    $handler->display->display_options['fields']['info']['label'] = '';
    $handler->display->display_options['fields']['info']['element_label_colon'] = FALSE;
    $handler->display->display_options['fields']['info']['format'] = 'key';
    $handler->display->display_options['fields']['info']['key'] = 'version';
    /* Field: Global: Custom text */
    $handler->display->display_options['fields']['nothing']['id'] = 'nothing';
    $handler->display->display_options['fields']['nothing']['table'] = 'views';
    $handler->display->display_options['fields']['nothing']['field'] = 'nothing';
    $handler->display->display_options['fields']['nothing']['label'] = '';
    $handler->display->display_options['fields']['nothing']['exclude'] = TRUE;
    $handler->display->display_options['fields']['nothing']['alter']['text'] = '[info_project]-[info]';
    $handler->display->display_options['fields']['nothing']['element_label_colon'] = FALSE;
    $handler->display->display_options['defaults']['filter_groups'] = FALSE;
    $handler->display->display_options['defaults']['filters'] = FALSE;
    /* Filter criterion: System: Type */
    $handler->display->display_options['filters']['type']['id'] = 'type';
    $handler->display->display_options['filters']['type']['table'] = 'system';
    $handler->display->display_options['filters']['type']['field'] = 'type';
    $handler->display->display_options['filters']['type']['value'] = array(
      'module' => 'module',
    );
    $handler->display->display_options['filters']['type']['group'] = 1;
    /* Filter criterion: System: Status */
    $handler->display->display_options['filters']['status']['id'] = 'status';
    $handler->display->display_options['filters']['status']['table'] = 'system';
    $handler->display->display_options['filters']['status']['field'] = 'status';
    $handler->display->display_options['filters']['status']['value'] = '1';
    $handler->display->display_options['filters']['status']['group'] = 1;
    /* Filter criterion: System: Drupal core */
    $handler->display->display_options['filters']['drupal_core']['id'] = 'drupal_core';
    $handler->display->display_options['filters']['drupal_core']['table'] = 'system';
    $handler->display->display_options['filters']['drupal_core']['field'] = 'drupal_core';
    $handler->display->display_options['filters']['drupal_core']['value'] = '0';
    $handler->display->display_options['filters']['drupal_core']['group'] = 1;
    $handler->display->display_options['filters']['drupal_core']['exposed'] = TRUE;
    $handler->display->display_options['filters']['drupal_core']['expose']['operator_id'] = '';
    $handler->display->display_options['filters']['drupal_core']['expose']['label'] = 'Drupal core';
    $handler->display->display_options['filters']['drupal_core']['expose']['operator'] = 'drupal_core_op';
    $handler->display->display_options['filters']['drupal_core']['expose']['identifier'] = 'drupal_core';
    $handler->display->display_options['filters']['drupal_core']['expose']['required'] = TRUE;
    $handler->display->display_options['filters']['drupal_core']['expose']['remember_roles'] = array(
      2 => '2',
      1 => 0,
      3 => 0,
      4 => 0,
      5 => 0,
      6 => 0,
    );
    /* Filter criterion: System: Name */
    $handler->display->display_options['filters']['name']['id'] = 'name';
    $handler->display->display_options['filters']['name']['table'] = 'system';
    $handler->display->display_options['filters']['name']['field'] = 'name';
    $handler->display->display_options['filters']['name']['operator'] = 'word';
    $handler->display->display_options['filters']['name']['exposed'] = TRUE;
    $handler->display->display_options['filters']['name']['expose']['operator_id'] = 'name_op';
    $handler->display->display_options['filters']['name']['expose']['label'] = 'Name';
    $handler->display->display_options['filters']['name']['expose']['operator'] = 'name_op';
    $handler->display->display_options['filters']['name']['expose']['identifier'] = 'name';
    $handler->display->display_options['filters']['name']['expose']['remember_roles'] = array(
      2 => '2',
      1 => 0,
      3 => 0,
      4 => 0,
      5 => 0,
      6 => 0,
    );
    $handler->display->display_options['path'] = 'enabled-modules/list';

    /* Display: Data export CSV */
    $handler = $view->new_display('views_data_export', 'Data export CSV', 'views_data_export_1');
    $handler->display->display_options['defaults']['query'] = FALSE;
    $handler->display->display_options['query']['type'] = 'views_query';
    $handler->display->display_options['query']['options']['distinct'] = TRUE;
    $handler->display->display_options['pager']['type'] = 'none';
    $handler->display->display_options['pager']['options']['offset'] = '0';
    $handler->display->display_options['style_plugin'] = 'views_data_export_csv';
    $handler->display->display_options['style_options']['provide_file'] = 1;
    $handler->display->display_options['style_options']['parent_sort'] = 0;
    $handler->display->display_options['style_options']['quote'] = 1;
    $handler->display->display_options['style_options']['trim'] = 0;
    $handler->display->display_options['style_options']['replace_newlines'] = 0;
    $handler->display->display_options['style_options']['header'] = 1;
    $handler->display->display_options['style_options']['keep_html'] = 0;
    $handler->display->display_options['defaults']['fields'] = FALSE;
    /* Field: System: Info */
    $handler->display->display_options['fields']['info']['id'] = 'info';
    $handler->display->display_options['fields']['info']['table'] = 'system';
    $handler->display->display_options['fields']['info']['field'] = 'info';
    $handler->display->display_options['fields']['info']['label'] = '';
    $handler->display->display_options['fields']['info']['exclude'] = TRUE;
    $handler->display->display_options['fields']['info']['element_label_colon'] = FALSE;
    $handler->display->display_options['fields']['info']['format'] = 'key';
    $handler->display->display_options['fields']['info']['key'] = 'version';
    /* Field: System: Project */
    $handler->display->display_options['fields']['info_project']['id'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['table'] = 'system';
    $handler->display->display_options['fields']['info_project']['field'] = 'info_project';
    $handler->display->display_options['fields']['info_project']['label'] = '';
    $handler->display->display_options['fields']['info_project']['alter']['alter_text'] = TRUE;
    $handler->display->display_options['fields']['info_project']['alter']['text'] = '[info_project]-[info]';
    $handler->display->display_options['fields']['info_project']['alter']['path'] = 'http://drupal.org/[info_project]';
    $handler->display->display_options['fields']['info_project']['alter']['external'] = TRUE;
    $handler->display->display_options['fields']['info_project']['element_label_colon'] = FALSE;
    $handler->display->display_options['fields']['info_project']['hide_alter_empty'] = FALSE;
    $handler->display->display_options['fields']['info_project']['system_info_project_link'] = 0;
    $handler->display->display_options['defaults']['filter_groups'] = FALSE;
    $handler->display->display_options['defaults']['filters'] = FALSE;
    /* Filter criterion: System: Type */
    $handler->display->display_options['filters']['type']['id'] = 'type';
    $handler->display->display_options['filters']['type']['table'] = 'system';
    $handler->display->display_options['filters']['type']['field'] = 'type';
    $handler->display->display_options['filters']['type']['value'] = array(
      'module' => 'module',
    );
    /* Filter criterion: System: Status */
    $handler->display->display_options['filters']['status']['id'] = 'status';
    $handler->display->display_options['filters']['status']['table'] = 'system';
    $handler->display->display_options['filters']['status']['field'] = 'status';
    $handler->display->display_options['filters']['status']['value'] = '1';
    /* Filter criterion: System: Drupal core */
    $handler->display->display_options['filters']['drupal_core']['id'] = 'drupal_core';
    $handler->display->display_options['filters']['drupal_core']['table'] = 'system';
    $handler->display->display_options['filters']['drupal_core']['field'] = 'drupal_core';
    $handler->display->display_options['filters']['drupal_core']['value'] = '0';
    $handler->display->display_options['path'] = 'enabled-modulles/csv';
    $handler->display->display_options['sitename_title'] = 0;
    $translatables['enabled_modules'] = array(
      t('Master'),
      t('Enabled Modules CSV'),
      t('more'),
      t('Apply'),
      t('Reset'),
      t('Sort by'),
      t('Asc'),
      t('Desc'),
      t('Display name'),
      t('[info_name] ([name])'),
      t('Project'),
      t('Enabled Modules'),
      t('Delimited list'),
      t('Enabled Modules LIst'),
      t('[info_project]-[info]'),
      t('Drupal core'),
      t('Name'),
      t('Data export CSV'),
    );



Then you grab the delimited list and just 
drush dl [the list]

or 

you grab the csv go to sublime text nad
ctr-h " with empty
nad the press ctr+j until everythin is inline


The list for to enable the modules we want to use the submodules