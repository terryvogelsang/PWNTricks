# PHP

>PHP is a server-side scripting language designed for web development but also used as a general-purpose programming language. It is originally created by Rasmus Lerdorf in 1994, the PHP reference implementation is now produced by The PHP Group.

Source : [Wikipedia](https://en.wikipedia.org/wiki/PHP)

But PHP is also known to adopt a lot of funny behaviors that can lead to security vulnerabilities !

## Dots in variable name

Reference : [](http://php.net/manual/en/language.variables.external.php)

```
**Note:**

Dots and spaces in variable names are converted to underscores. For example <input name="a.b" /> becomes $_REQUEST["a_b"].
```