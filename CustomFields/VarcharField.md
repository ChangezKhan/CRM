# Create custom varchar field

### First create a blank file named `custom_varchar_field.php` in following location

    custom/Extension/modules/<MODULE_NAME>/Ext/Vardefs/custom_varchar_field.php

### Now add following code to above newly created `custom_varchar_field.php` file
	
	<?php
	
	$GLOBALS["dictionary"]["<MODULE_NAME>"]['fields']['<NAME_OF_FIELD>'] = 
		array (
			'required' => '0',
			'name' => '<NAME_OF_FIELD>',
			'vname' => 'LBL_<NAME_OF_FIELD>',
			'type' => 'varchar',
			'massupdate' => '0',
			'default' => NULL,
			'comments' => '',
			'help' => '',
			'importable' => 'false',
			'duplicate_merge' => 'disabled',
			'duplicate_merge_dom_value' => '0',
			'audited' => 0,
			'reportable' => 0,
			'len' => '36',
		);
		
	?>
	
### Now, do a "Quick Repair & Rebuild" and you're done.

