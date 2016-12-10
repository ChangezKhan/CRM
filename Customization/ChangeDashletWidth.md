#Change width of dashlet on Home page

### To change the width of dashlet on Home page, we need to make changes in following file: 

	include\MySugar\tpls\MySugar.tpl

### First find the `div` with `pageContainer` ID. Now in `foreach` loop, find `td` where `width` is mentioned as `$data.width` and replace this `$data.width` with any number of percentage, such as '50%'.

### And that's it.
