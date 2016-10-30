# How to redirect using SugarCRM way

### We can use the following code to redirect to any page using SugarCRM way.

    $params = array(
        'module'=> 'Accounts',
	'action'=>'DetailView',
    );

    SugarApplication::redirect("index.php?" .http_build_query($params));
