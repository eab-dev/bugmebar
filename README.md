#bugmebar

eZ Publish extension providing a cookie based pop-up notice.
Based on [jquery.bugmebar](https://github.com/weare2ndfloor/BugMeBar)
and [jquery.cookie](https://github.com/carhartl/jquery-cookie)

##Copyright

Portions copyright Enterprise AB Ltd (c) 2014 http://eab.uk
jquery.bugmebar copyright [Chris Wharton](mailto:hello@weare2ndfloor.com) 
jquery.cookie copyright [Klaus Hartl](https://twitter.com/carhartl)

##License

GPL 2.0

##Requirements

* eZ Publish 4 or eZ Publish 5 Legacy Edition.
* ezjscore extension

##Install

Install and activate the extension in the usual way:

1. Copy the `bugmebar` folder to the `extension` folder.

2. Edit `settings/override/site.ini.append.php`

3. Under `[ExtensionSettings]` add:

    ActiveExtensions[]=bugmebar

4. Reload the autoload arrays

    bin/php/ezpgenerateautoloads.php

5. Clear the cache:

    bin/php/ezcache.php --clear-all

##Usage:

To use this add some code to `pagelayout.tpl` in your design extension:

* Add class `bugmebar` to the div that should have the notice added e.g. `<div id="page" class="bugmebar" ....>`

* Add Javascript to call bugbear. For example:

    {literal}
        <script type="text/javascript">
        //<![CDATA[
            jQuery(document).ready(function(){
                jQuery('div#page').bugme({
                remember: true, // this stores a cookie to remember cancellation of bugme bar
                expireIn: 28, // set expiry of remember cookie (in days)
                cookieName:"eab_message_cookie_1",
                message: "Please note that, from April, access to parts of this website and associated resources will only be available to members. <a target='_blank' href='http://www.eab.co.uk'>Please click here for more details</a>" // message that goes inside the bug me bar
                });
            });
        //]]>
        </script>
    {/literal}

