# UserPath Documentation
Our documentation - for the time being. If you have any questions, please don't hesitate to email support@userpath.co - we will get back to you as quickly as possible!

## Click to Call Widget

### CSS
You can over write our css for our widgets.

### Using dynamic phone numbers
We allow you to use dynamic phone numbers on the front end if you don't want to import all of your phone numbers into UserPath's interface. We allow you do this using shared secrets & signing the options for your call with that secret. You can grab your secret in your account settings here: http://alpha.userpath.co/account/settings/profile/

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

```python
import re
import hashlib 

def genkey(pub, to):
    pub = "".join(re.findall(r'\d+', pub))
    to = "".join(re.findall(r'\d+', to))
    secret_key = 'Your Key Here'
    return hashlib.md5("{0}-{1}-{2}".format(to, secret_key, pub)).hexdigest()
```

```ruby
require 'digest'
 
def genkey(pub, to)
  pub.gsub!(/\D/, '')
  to.gsub!(/\D/, '')
  secret_key = 'Your Key Here'
  Digest::MD5.hexdigest "#{to}-#{secret_key}-#{pub}"
end
```

### Using auto-detect
ctc-num

## App Download Widget

Something
