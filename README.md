# CSRF
Introduction


CSRF Revision
What is CSRF:

CSRF stands for Cross Site Request Forgery.


CSRF Severity:

CSRF is a critical vulnerability since an attacker can permanently take over a user's account.



Testing CSRF Vulnerabilities:

Make 2 accounts, one is of victim and another of attacker

Sign In with attacker account and generate a malicious link also called as CSRF POC

Send the PoC to the victim

Sign In with the victim's account and open the link.

If successful i.e. data changes, BOOM you proved the web application vulnerable to CSRF



Alternative to Burp: CSRF PoC Generator:

Burp Suite Community Edition does not come with CSRF PoC Generator an alternative tool which you can use can be found here : https://github.com/merttasci/csrf-poc-generator

Which can generate PoC for any HTTP request

Steps:

git clone https://github.com/merttasci/csrf-poc-generator

python -m SimpleHTTPServer 8080

Keep the terminal running and on the browser enter: localhost:8080



Where can we hunt for CSRF?

Pages where sensitive data such as Email Id, Password, User Name can be changed

Remember: CSRF on Login/Logout is not Sensitive and Out Of Scope



How can we perform an Account Take Over using CSRF?

If a website is vulnerable to CSRF we can change the Email ID and/or password of the user

thus performing a complete account take over of the user.

CSRF Chaining with XSS:

A simple payload of getting the cookie using XSS and passing the cookie to CSRF PoC,and then sending the malicious link to the victim can get you CSRF!



CSRF Tricks:

Some web applications are vulnerable to CSRF when their request method is changed from GET to POST and vice-versa, so always try to change the request method

Remove Tokens: Sometimes removing the token param from the PoC, can give you a valid csrf.

Some web applications have the CSRF Tokens as static and dynamic and hence this also can lead you to CSRF.

Some web applications check CSRF Tokens based on entropy length. Keep the entropy length same and you win!



CSRF Mitigations:

Check if the request is coming from a legitimate source or not.

Always use dynamic/rolling tokens to protect from CSRF.

Authenticate a request by some kind of protection which can be xsrf, csrf tokens.
