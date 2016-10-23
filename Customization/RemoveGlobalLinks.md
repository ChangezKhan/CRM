#Remove unwanted Global Links

### To remove the un-necessary global links, first copy `globalControlLinks.php` file from `include\` directory to `custom\include\` directory.

### After copying file, we have just have to comment following arrays:

    $global_control_links['employees']
    $global_control_links['training']
    $global_control_links['help']
    $global_control_links['about']

### And that's it.
