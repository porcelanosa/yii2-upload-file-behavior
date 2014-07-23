Upload File Behavior for Yii2
========================
Behavior for simplifies file upload for Yii2.

Installation
------------
Copy `UploadFileBehavior.php` to your `app/components` folder.

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
use app\components\UploadFileBehavior;

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
