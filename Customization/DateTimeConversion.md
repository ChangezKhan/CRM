# Datetime conversion by SugarCRM way

### In the following file, there is lot's of functions which Sugar uses for its datetime functionality.

    include\TimeDate.php

### There is one function, named `_convert` which Sugar uses to convert datetime from User specified format to Database format and vice-versa. But we can't use this function as it is a `Protected` function. So to access this `protected` function, we will create one new `public` function `convert_datetime` and in this function we will call this SugarCRM's `_convert` function.

    /**
     *
     * To access basic conversion function (_convert) by Sohan
     *
     * Converts between two string dates in different formats and timezones
     *
     * @param string $date
     * @param string $from_format
     * @param DateTimeZone $from_timezone
     * @param string $to_format
     * @param DateTimeZone $to_timezone
     * @return string
     */
    public function convert_datetime($date, $from_format, $from_timezone, $to_format, $to_timezone)
    {
        $new =  $this->_convert($date, $from_format, $from_timezone, $to_format, $to_timezone);
        return $new;
    }
	
### And that's it. We just need to include this file in whichever file we want and call our newly created function and pass required parameters.