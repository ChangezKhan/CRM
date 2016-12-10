#Remove unwanted Global Links

### To remove the un-necessary global links, we need to make changes in following file: 

	include\globalControlLinks.php

### In this file, we have just have to comment following arrays:

    $global_control_links['employees']
    $global_control_links['training']
    $global_control_links['help']
    $global_control_links['about']

### And that's it.
