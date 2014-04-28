### LJ Cookies plugin for Craft CMS

A simple plugin for setting and retrieving cookies from within [Craft CMS](http://buildwithcraft.com) templates.

**Installation**

1. Unzip file 
2. Place `lj_cookies` directory into your `craft/plugins` directory
3. Install plugin in the Craft Control Panel under Settings > Plugins

###Setting cookies###

    {% do craft.lj_cookies.set( NAME, VALUE, EXPIRE, PATH, DOMAIN, SECURE, HTTPONLY) %}

This plugin acts as a wrapper for the PHP `setcookie` function:

More info: (http://php.net/manual/en/function.setcookie.php)

**Examples**

    {% do craft.lj_cookies.set('myname', 'myvalue') %}
    {# Sets a cookie to expire at end of session. #}

    {% do craft.lj_cookies.set('myname', 'myvalue', now | date_modify("+1 hour").timestamp ) %}
    {# Sets a cookie to expire in an hour. #}

    {% do craft.lj_cookies.set('myname', 'myvalue', now | date_modify("+30 days").timestamp ) %}
    {# Sets a cookie to expire in 30 days. #}
	
    {% do craft.lj_cookies.set('myname', 'myvalue', '', '/' ) %}
    {# Cookie available for entire domain. #}

    {% do craft.lj_cookies.set('myname', 'myvalue', '', '/foo/' ) %}
    {# Cookie available within /foo/ directory and sub-directories. #}

###Retrieving cookies###

    {{ craft.lj_cookies.get( NAME ) }}
	{# Note that we're using 'get' to retrieve. #}

**Example**

    {% do craft.lj_cookies.set('user', 'Lewis', '', '/') %}
	{# Set the cookie using 'set' #}

    <p>Howdy, {{ craft.lj_cookies.get('user') }}</p>
	{# Retrieve the cookie's value using 'get' #}
	
###Deleting cookies###

	{% do craft.lj_cookies.set('myname', '') %}
	{# Delete a cookie by setting an empty value #}

**Tested on**

+ Craft 1.1
+ Craft 1.2
+ Craft 1.3
