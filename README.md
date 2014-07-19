Upload File Behavior for Yii2
========================

Behavior for simplifies file upload for Yii2.

Installation
------------
The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require "himiklab/yii2-upload-file-behavior" "*"
```
or add

```json
"himiklab/yii2-upload-file-behavior" : "*"
```

to the require section of your application's `composer.json` file.

Usage
-----

In view:

```php
use yii\widgets\ActiveForm;

<?php $form = ActiveForm::begin(['options' => ['enctype' => 'multipart/form-data']]); ?>

<?= $form->field($model, 'picture')->fileInput() ?>

<div class="form-group">
    <?=
    Html::submitButton(
        $model->isNewRecord ? 'Create' : 'Update',
        ['class' => $model->isNewRecord ? 'btn btn-success' : 'btn btn-primary']
    ) ?>
</div>

<?php ActiveForm::end(); ?>
```

In AR model:

```php
use himiklab\uploadfile\UploadFileBehavior;

public function behaviors()
{
    return [
        'file' => [
            'class' => UploadFileBehavior::className(),
            'attributeName' => 'picture',
            'savePath' => '@webroot/uploads',
            'generateNewName' => true,
            'protectOldValue' => true,
        ],
    ];
}
```
