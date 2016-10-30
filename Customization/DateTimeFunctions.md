# Various datetime functions

### Get 'datetime' format of current user

    $datetime_format = $timedate->get_date_time_format($current_user);

### Get 'date' format of current user

    $date_format = $current_user->getPreference('datef');

### Get 'Timezone' fo current user

    $timezone = $timedate->getInstance()->userTimezone();
