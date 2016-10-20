# Create custom relate field

### Let's consider we need to create a relate of module `A` in module `B`. Then, first create a blank file named `custom_relate_field.php` in following location

    custom/Extension/modules/B/Ext/Vardefs/custom_relate_field.php

### Now add following code to above newly created `custom_relate_field.php` file
	
	<?php
	
	$GLOBALS["dictionary"]["B"]['fields']['A_id'] = 
		array (
		  'required' => '0',
		  'name' => 'A_id',
		  'vname' => 'LBL_A_ID',
		  'type' => 'id',
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

	$GLOBALS["dictionary"]["B"]['fields']['A_name'] = 
		array (
		  'required' => '0',
		  'source' => 'non-db',
		  'name' => 'A_name',
		  'vname' => 'LBL_A_NAME',
		  'type' => 'relate',
		  'massupdate' => '0',
		  'default' => NULL,
		  'comments' => '',
		  'help' => '',
		  'importable' => 'false',
		  'audited' => 0,
		  'reportable' => 0,
		  'len' => '255',
		  'id_name' => 'A_id',
		  'ext2' => 'A',
		  'module' => 'A',
		  'quicksearch' => 'enabled',
		  'studio' => 'visible',
		);
		
	?>
	
### Now, do a "Quick Repair & Rebuild" and you're done.

