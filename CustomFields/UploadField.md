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

### Now, open `editviewdefs.php` file of following location:

    custom/modules/<module_name>/metadata/editviewdefs.php

### Now, add following code to `form` array: 

    'enctype' => 'multipart/form-data',

### Now, do a "Quick Repair & Rebuild". 

### After this, you can see this field in `Studio`. You may change its label name and move into `Edit` or `Detail` view, as your need.

### Now for all modules, download attachment will work smoothly, except `Cases` module. To work with `Cases` modules, we will need to tweak `download.php` file a little bit. You will find this find in root folder of your CRM.

    <CRM>/download.php

### Now, add following lines of code after `$bean_name = $beanList[$module];`, 

    if($module == "Cases")
    {
        $bean_name = "Case";
    }

### And, add another `elseif` to fetch `filename` and `file_mime_type` from `cases` table

    elseif($file_type == 'cases') 
    {
        $query = "SELECT filename name, file_mime_type FROM cases ";
	$query .= "WHERE cases.id = '" . $db->quote($_REQUEST['id']) ."'";
    }

### After this, you can download attachment for `Cases` module also.

