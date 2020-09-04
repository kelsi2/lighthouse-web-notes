# HTTP Cookies & User Authentication

## Topics
### HTTP and cookies
### Render pages differently based on language preference
### Register user with email and password

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w03d03)

### Why do we need cookies?
* HTTP is stateless (has no memory)
* Cookies maintain information between requests
* Browser automatically sends cookies with every request
* Cookies stay until we (the user) clear them or the server automatically clears them (times out e.g. a bank)
* Cookie is a key value pair (user id, language preference, etc.)
* Domain specific (fb, google, twitter, etc. all have individual cookies that don't automatically go to a different domain when you move)