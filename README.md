Rack::SSL
=========

This branch enhances Rack::SSL to enforce redirects to a subdomain if disallow_no_subdomain is set.
As an example, in the environments/production.rb file, you'd probably have the following set for Rack:SSL

 config.middleware.insert_before ActionDispatch::Cookies, Rack::SSL,:port=>443,:host=>'www.7vals.com'

Assuming your host is www.7vals.com 
If a user types in https://7vals.com (and for certain browsers that ignore protocol AND subdomain redirects), 
they will still be able to access the site. This will be an issue if you've setup cookies to be subdomain specific

To ensure users are not able to use 'no subdomain based url', use the option disallow_no_subdomain ie:

  config.middleware.insert_before ActionDispatch::Cookies, Rack::SSL,:port=>443,:host=>'www.7vals.com',:disallow_no_subdomain=>true



Force SSL/TLS in your app.

1. Redirects all "http" requests to "https"
2. Set `Strict-Transport-Security` header
3. Flag all cookies as "secure"

Usage
-----

    use Rack::SSL

