WritesDown CMS Access Manager
============================


Configuration
--------------

backend/config/main.php

```
'as access' => [
     'class' => '\modules\access\backend\components\AccessControl',
     'allowActions' => [
        'site/login',
    ],
],
...,

'components' => [
    'authManager' => [
        'class' => 'yii\rbac\DbManager', // only support DbManager
        'assignmentTable'=> '{{%auth_assignment}}',
       	'itemChildTable'=> '{{%auth_item_child}}',
       	'itemTable'=> '{{%auth_item}}',
       	'ruleTable'=> '{{%auth_rule}}',
    ],
],
```

Migration
----------
```
yii migrate --migrationPath=@modules/access/backend/migrations
```

Menu
-----

backend/views/layouts/main-sidebar.php

```
$adminSiteMenu[60] = [
        		'label'   => Yii::t('writesdown', 'Access Manager'),
        		'icon'    => 'fa fa-cogs',
        		'items'   => [
        				[
        						'icon'  => 'fa fa-circle-o',
        						'label' => Yii::t('writesdown', 'All Roles'),
        						'url'   => ['/access/role/index'],
        				],
        				[
        						'icon'  => 'fa fa-circle-o',
        						'label' => Yii::t('writesdown', 'All Route'),
        						'url'   => ['/access/route/index'],
        				],
        		],
        		'visible' => Yii::$app->user->can('administrator'),
        ];
```