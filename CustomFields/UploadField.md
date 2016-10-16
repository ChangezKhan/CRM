# Create custom file upload field

### First create a blank file named `upload_file.php` in following location

    custom/Extension/modules/<module_name>/Ext/Vardefs/upload_file.php

### Now add following code to above newly created `upload_file.php` file

    <?php

    /* Create a custom file upload field*/
    
    $dictionary['Case']['fields']['file_mime_type'] = array(
        'name' => 'file_mime_type',
        'vname' => 'LBL_FILE_MIME_TYPE',
        'type' => 'varchar',
        'len' => '100',
        'importable' => false,
    );
    
    $dictionary['Case']['fields']['file_url'] = array(
    	'name'=>'file_url',
        'vname' => 'LBL_FILE_URL',
        'type'=>'function',
        'function_class'=>'UploadFile',
        'function_name'=>'get_upload_url',
        'function_params'=> array('$this'),
        'source'=>'function',
        'reportable'=>false,
        'importable' => false,
    );
    
    $dictionary['Case']['fields']['filename'] = array(
    	'name' => 'filename',
        'vname' => 'LBL_FILENAME',
        'type' => 'file',
        'dbType' => 'varchar',
        'len' => '255',
        'reportable'=>true,
        'importable' => false,
    );

### Now, add following code to `editviewdefs.php` file in following location:

    custom/modules/<module_name>/metadata/editviewdefs.php

#### Code: 

    'enctype' => 'multipart/form-data',

### Now, do a "Quick Repair & Rebuild". 


