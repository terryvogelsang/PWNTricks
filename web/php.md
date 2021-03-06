# PHP

> PHP is a server-side scripting language designed for web development but also used as a general-purpose programming language. It is originally created by Rasmus Lerdorf in 1994, the PHP reference implementation is now produced by The PHP Group.

Source : [Wikipedia](https://en.wikipedia.org/wiki/PHP)

But PHP is also known to adopt a lot of funny behaviors that can lead to security vulnerabilities !

## Dots in variables names

### Tag\(s\)

* WAF Bypass

### Reference\(s\)

[Variables From External Sources - PHP Manual](http://php.net/manual/en/language.variables.external.php)

### Details

Typically, PHP does not alter the names of variables when they are passed into a script. However, it should be noted that the dot \(period, full stop\) is not a valid character in a PHP variable name. For the reason, look at it:

```php
<?php
$varname.ext;  /* invalid variable name */
?>
```

Now, what the parser sees is a variable named `$varname`, followed by the string concatenation operator, followed by the barestring \(i.e. unquoted string which doesn't match any known key or reserved words\) 'ext'. Obviously, this doesn't have the intended result.

For this reason, **it is important to note that PHP will automatically replace any dots in incoming variable names with underscores.**

The full list of field-name characters that PHP converts to \_ \(underscore\) is the following \(not just dot\):

chr\(32\) \( \) \(space\) chr\(46\) \(.\) \(dot\) chr\(91\) \(\[\) \(open square bracket\) chr\(128\) - chr\(159\) \(various\)

PHP irreversibly modifies field names containing these characters in an attempt to maintain compatibility with the deprecated register\_globals feature.

As dots and spaces in variable names are converted to underscores, `<input name="a.b" />` becomes `$_REQUEST["a_b"].`

## Common Obfuscation Techniques

```php
$y = str_replace('n', 'e', 'systnm');
$y("ls /");
```

