# Safari X-Success

This is an empty shell page with some JavaScript in it that allows Mobile Safari on iOS to mimic Chrome on iOS's x-success back button behavior. It is based on [Greg Pierce's](http://agiletortoise.com/blog/2014/02/28/mimic-x-callback-url-in-mobile-safari/) post to do the same with iframes. This solution uses the JavaScript history API instead of an iframe, which feels a bit cleaner to me.

## Usage

The URL scheme is identical to [Greg's post](http://agiletortoise.com/blog/2014/02/28/mimic-x-callback-url-in-mobile-safari/), with one small difference being the URL itself. Point to the raw Github version of this page instead of to one hosted on Agile Tortoise.

````
https://rawgithub.com/josephschmitt/safari-x-success/master/callback.html?
	url=[[selection]]
	&x-success={{tweetbot://}}
````

This will open up Mobile Safari and instantly redirect the browser to the url at the url parameter. However, when you hit the back button to return to the initial page, it'll bounce you back to whatever url scheme is defined in x-success. The only downside to this system is there is no way to close the original page automatically via JavaScript like Chrome does. If anyone has any ideas how to do this, feel free to pull request.