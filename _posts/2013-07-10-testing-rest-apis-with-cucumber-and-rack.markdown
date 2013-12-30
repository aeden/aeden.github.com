---
layout: post
title: "Testing REST APIs With Cucumber and Rack"
date: 2013-07-10 15:48
comments: true
categories: 
---
_Author's note: This is a repost of an post I originally wrote in 2011. I'm reposting it by request. Enjoy!_

This evening Corey and I sat down and started looking into how we could make the tests live again. First we attempted to use Capybara directly, but ran into issues when trying to set HTTP headers. The DNSimple API uses Basic HTTP Authentication and thus we needed to set the header for that. We also need to set the Content-Type and Accept headers to ensure that Rails handles the input and output correctly. After peeling back some layers of the Capybara onion we landed upon Rack::Test. When using Rack, Capybara delegates request and response handling down to <a href="http://github.com/brynary/rack-test">Rack::Test</a>. At this point we decided to see if we could use Rack::Test directly in our step definitions, and it worked like a charm.

Rack::Test has a module called Rack::Test::Methods that can be mixed into a class to provide it with methods for get, post, put, delete as well as last_request, last_response, header and more. We mixed Rack::Test::Methods into the Cucumber world at the top of our API steps file like so:

<script src="https://gist.github.com/aeden/660319.js"></script>

Then our steps could simply call the Rack::Test methods directly. For example, here&#8217;s how to send the HTTP Basic Auth header:

<script src="https://gist.github.com/aeden/660321.js"></script>

And to set content type and accept headers:

<script src="http://gist.github.com/aeden/660323.js"></script>

And finally to actually send requests and test the responses. The entire api\_steps.rb as it is right now looks like this:

<script src="http://gist.github.com/aeden/660331.js"></script>

And here is an example of a Cucumber feature that uses the API steps:

<script src="http://gist.github.com/aeden/660337.js"></script>

I doubt we&#8217;ve ended up with the ultimate final set of steps that can be used repeatedly for testing RESTful APIs, however I think it is an excellent start. I&#8217;m still on the fence about how to check the response body, specifically whether it is better to match the response body as a string or to actually parse it and write custom steps for each of the different types of objects, but time will tell.

As usual pairing with Corey resulted in some good code, a usable solution and something that I think others will benefit from as well.
