# How to add custom hyper link to any field in detail view of any module

### First we will add following code to a field, on which we want hyper link on it to following file

    custom\modules\<MODULE_NAME>\metadata\detailviewdefs.php

Now find the add the following code to an array of field, on which you want to see hyper link

    'customCode' => '{$CSTM_URL}'

### Now, add following code to `view.detail.php` and `view.list.php` file

    $link = "index.php?module=<MODULE_NAME>&action=DetailView&record={$this->bean-><ID_OF_ANY_FIELD>}";
    $field = $this->bean-><VALUE_OF_FIELD>;
    $custom_url = "<a href='" .$link ."' >" .$field ."</a>";
    $this->ss->assign("CSTM_URL", $custom_url);
