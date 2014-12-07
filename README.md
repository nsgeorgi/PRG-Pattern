PRG-Pattern
===========

Post - Redirect - Get Pattern

For further information , try wikipedia http://en.wikipedia.org/wiki/Post/Redirect/Get

The “do you want to resend the POST data to the website again?” error message a user gets when they try to refresh or go back to a page really scares them. Understandably, since the browser often says “this could mean you’ll pay for the item twice!”.

The first way to fix that is by sending all form data over an AJAX request. But if the user has javascript disabled then you’ll need to fall back to my next suggestion anyway.

The POST/REQUEST/GET (PRG) pattern removes that possibility by never allowing the user to fall onto a page which POST data has been sent to. Putting it simply, whenever you want POST data, you take it and then immediately redirect them.

You do the redirect by using a HTTP1.1 303, and although that sounds a little hacky it’s what was intended for that status to be used for.


Redirection
To avoid the double submit problem it is necessary to split the validation page in two. The first will only validade and commit to the database without any interaction with the client browser and the second will give the client the confirmation message.

The flow direction will be: register.php page -> POST to validate.php -> Redirect/GET to confirmation.php

