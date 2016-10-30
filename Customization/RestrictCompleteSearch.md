# How to restrict complete search 

### First copy `view.list.php` file from following location to a custom directory of a module

    include\MVC\View\views\view.list.php

### Now in `view.list.php` file, in `listViewProcess` function, add following lines of code

    global $current_user;

    $check_search = array_filter($this->lv->searchColumns);

    if (empty($check_search)) 
    {
        echo "<b><font color='red'>Complete Search Restricted</font></b>";
	return;	
    }
