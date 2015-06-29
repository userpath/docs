# UserPath Documentation
Our documentation - for the time being. If you have any questions, please don't hesitate to email support@userpath.co - we will get back to you as quickly as possible!

## Click to Call Widget

### CSS Selectors for overwriting styles
You can over write our css for the Click to Call widget. The classes vary by layout. Always remember that `:before` & `:after` selectors are your friends :)

All layouts:
- `.widgetctc-txt-field` is used on all text fields; name & phone number to be exact.
- `.widgetctc-name-field` is used only on the name field.
- `#widgetctc-phone-num-field` is used only on the phone number field.
- `.widgetctc-btn` is used for the submit button

Auto-detect:
- `.widget_ctc_auto_num` is used for the phone number button when that option is selected
- `.widget-ctc-webui-popover-title` is used for the h3 title on the form in the popover

Drop-in:
- `.widgetctc_form` is used for the form container
- `.widgetctc_form h2` is used for form title

Bottom-bar:
- `.widget_ctc_blurb` is used for the div containing the title and blurb
- `.widget_ctc_blurb h3` is used for targeting the title of the blurb
- `.widget_ctc_blurb p` is used for targeting the body of the blurb
- `.widget_ctc_bar_form` is used for the form container

### Using dynamic phone numbers
We allow you to use dynamic phone numbers on the front end if you don't want to import all of your phone numbers into UserPath's interface. We allow you do this using shared secrets & signing the options for your call with that secret. You can grab your secret in your account settings here: http://alpha.userpath.co/account/settings/profile/

The `pub` number shows up on caller id for the person that just requested a call while the `to` number is what we call when trying to connect the person that just requested a call to.

#### PHP implementation
- `$pub` is the number you'd like to display when calling the user filling out the click to call form.
- `$to` is most often a phone number where someone from your company can be reached. It's really just the number where we expect a human to pick up that we can connect to the user that filled out the click to call form.
- `$secret_key` is the secret key we just talked about. You can find yours here: http://alpha.userpath.co/account/settings/profile/

```php
<?php
function clean_number($num){
	return preg_replace("/[^0-9]/","", $num);
}

function genkey($pub, $to){
	$pub = clean_number($pub);
	$to = clean_number($to);
	$secret_key = 'Your Key Here'; // do not share
	return md5($to."-".$secret_key."-".$pub);
}
?>
```

#### Python implementation
- `pub` is the number you'd like to display when calling the user filling out the click to call form.
- `to` is most often a phone number where someone from your company can be reached. It's really just the number where we expect a human to pick up that we can connect to the user that filled out the click to call form.
- `secret_key` is the secret key we just talked about. You can find yours here: http://alpha.userpath.co/account/settings/profile/
```python
import re
import hashlib 

def genkey(pub, to):
    pub = "".join(re.findall(r'\d+', pub))
    to = "".join(re.findall(r'\d+', to))
    secret_key = 'Your Key Here'
    return hashlib.md5("{0}-{1}-{2}".format(to, secret_key, pub)).hexdigest()
```

#### Ruby implementation
- `pub` is the number you'd like to display when calling the user filling out the click to call form.
- `to` is most often a phone number where someone from your company can be reached. It's really just the number where we expect a human to pick up that we can connect to the user that filled out the click to call form.
- `secret_key` is the secret key we just talked about. You can find yours here: http://alpha.userpath.co/account/settings/profile/
```ruby
require 'digest'
 
def genkey(pub, to)
  pub.gsub!(/\D/, '')
  to.gsub!(/\D/, '')
  secret_key = 'Your Key Here'
  Digest::MD5.hexdigest "#{to}-#{secret_key}-#{pub}"
end
```

Once you have this function/method in place, call it by placing the `pub` number in the `data-ctc-pub-number` attribute, the `to` number in the `data-ctc-to-number` attribute & the resulting hash in the `data-ctc-authkey` attribute like so:
```php
<?php
require('genkey.php');
$company_num = "844-362-3596";
?>
<script data-ctc-widget="1" data-ctc-pub-number="<?= $company_num; ?>" data-ctc-to-number="<?= $company_num; ?>" data-ctc-authkey="<?= genkey($company_num, $company_num); ?>">
    /*{literal}<![CDATA[*/
    var WidgetCTC = window.WidgetCTC || {};
    var p = window.location.protocol == 'https:' ? 'https:' : 'http:' ;
 
    (function() {
        var script = document.createElement('script');
        script.async = true;
        script.src   = p+'//assets.userpath.co/js/0d9f92bdd748d70dabfab3750f2139a2/click_to_call.min.js';
       
        var entry = document.getElementsByTagName('script')[0];
        entry.parentNode.insertBefore(script, entry);
    })();
    /*]]>{/literal}*/
</script>
```


### Using auto-detect
We allow you to turn anything into a clickable thing that pops up the click to call form; things like buttons, images, links, etc. If you use this feature, then auto-detect will not search the entire page for strings that look like phone numbers it will only look for elements with attribute `data-ctc-auto`. So add `data-ctc-auto="true"` to any item you'd like to trigger the click to call process. 

## App Download Widget

### CSS Selectors for overwriting styles
You can over write our css for the App download widget. The classes vary by layout. Always remember that `:before` & `:after` selectors are your friends. :)

All layouts:
- `.widgetctc-txt-field` is used on all text fields; just phone number to be exact.
- `.intl-tel-input` wraps the phone number field
- `.widgetctc-btn` is used for the submit button

Drop-in:
- `.widgetsms_form_wrapper` is used to encapsulate the title and form
- `#widgetsms_form h2` is used for form title
