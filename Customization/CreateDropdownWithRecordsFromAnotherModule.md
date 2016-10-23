# Create custom relate field where options built from records from another modules

### Consider, we have two modules `A` & `B`. And we want to show all records of module `A`, to show in module `B` as a dropdown. So, first we will create a logic hook in module `A` to get all records and store it into any dropdown. At first, we need to create new dropdown using `Dropdown Editor`, so we can use it in our logic hook file.

### This is following code you should add to logic hook file:

    <?php
	
	if(!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');
		
	require_once('modules/ModuleBuilder/MB/ModuleBuilder.php');
	require_once('modules/ModuleBuilder/parsers/parser.dropdown.php');
	
	/**
	* Motive : To update the Dropdown editor with the new record as Dropdown using After save logic hook
	*/

	class StudioUpdate 
	{
		function save_dd($dd_name,$new_dd_arr)
		{
			$parser = new ParserDropDown();
			$params = array();
			$_REQUEST['view_package'] = 'studio';
			$params['view_package'] = 'studio';
			$params['dropdown_name'] = $dd_name;
			$params['dropdown_lang'] = 'en_us';
			$json = getJSONobj();
			$params['list_value'] = $json->encode($new_dd_arr);
			$parser->saveDropDown($params);
		}

		function StudioUpdate($bean,$arg,$events) 
		{
			global $db;

			$related_queue_arr = array();
			$related_queue_arr[''] = '';
			
			$dropdown_list_name = '<DropDown_List_Name>'; //DropDown List name
			$properties['options'] = $dropdown_list_name;

			$selectQueue_list = "SELECT id,name FROM campaigns WHERE deleted=0";
			$selectQueue_list_res = $db->query($selectQueue_list);
			$new_dd_arr[] = array('','');
			
			while($selectQueue_list_res_row = $db->fetchByAssoc($selectQueue_list_res))
			{
				$related_queue_arr[$selectQueue_list_res_row['id']] = $selectQueue_list_res_row['name'];
				$new_dd_arr[]=array($selectQueue_list_res_row['id'],$selectQueue_list_res_row['name']);
			}
						
			$GLOBALS['app_list_strings'][$dropdown_list_name] = $related_queue_arr;
			$this->save_dd($properties['options'],$new_dd_arr);
		
		}
	}
    ?>
