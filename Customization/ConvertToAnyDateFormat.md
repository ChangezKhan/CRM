# How to convert any date/datetime format by SugarCRM way

### SugarCRM uses `_convert` function declared in following file. to convert any date/datetime format to any format:

    include\TimeDate.php

### But, if you see, this is a `protected` function and we can access this from the very same class or subclasses, but not from the outside of class. So to use this function we need to create a one `public` function in the same file and triggers the same `protected` function `_convert`.

### Add following `public` function to above mentioned file

    /**
    *
    * To access basic conversion function (_convert)
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
	$datetime =  $this->_convert($date, $from_format, $from_timezone, $to_format, $to_timezone);
        return $datetime;
    }

### Now, we can access this function using `global` variable `$timedate`.
