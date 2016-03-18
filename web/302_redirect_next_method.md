# HTTP method on a 302 redirect

If you send a POST to a web server, which responds with a 302 redirect, which HTTP method should be used by the browser next (while redirecting to the new uri)? 

This is what [StackOverflow](http://stackoverflow.com/questions/17605915/what-is-the-correct-behavior-expected-of-an-http-post-302-redirect-to-get) and the [HTTP spec](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3) says. 

> If the 302 status code is received in response to a request other than GET or HEAD, the user agent **MUST NOT automatically redirect the request unless it can be confirmed by the user**, since this might change the conditions under which the request was issued.

This means that the 2nd request made by the browser should be the same as the first request, i.e., if the first request was a POST, then the 2nd request to the redirect uri should also be a POST. However, this is not what modern browsers do.  

This is why there is an updated spec that indicates: 

> Note: RFC 1945 and RFC 2068 specify that the client is not allowed to change the method on the redirected request. However, most existing user agent implementations treat 302 as if it were a 303 response, performing a GET on the Location field-value regardless of the original request method. The status codes 303 and 307 have been added for servers that wish to make unambiguously clear which kind of reaction is expected of the client.

Basically: 

1. 303 redirect => Next request should be a GET.
1. 307 redirect => Next request should be a POST.

However, for backwards compatibility reasons, we still use 302 redirects.
