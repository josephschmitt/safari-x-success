# Safari X-Success

This is an empty shell page with some JavaScript in it that allows Mobile Safari on iOS to mimic Chrome on iOS's x-success back button behavior. It is based on [Greg Pierce's post](http://agiletortoise.com/blog/2014/02/28/mimic-x-callback-url-in-mobile-safari/) to do the same with iframes. This solution uses the JavaScript history API instead of an iframe, which feels a bit cleaner to me.

## Usage

The URL scheme is very similar to Greg's post, with two small differences: 

1. The URL itself point to the callback.html page in this repository directly. This is mostly for security, so you can see the source code on Github and trust I'm not stealing your browser sessions :-).
2. Use a hash (#) instead of query parameter (?) for the parameters. This is so that Safari treats all of the pages with different parameters as a single page, and will just re-load the page if it's already open in your browser instead of opening up a new page. This means you'll only ever have at most one x-success browser window open instead of a bunch. This should help mitigate the problem with not being able to close the window when jumping back to the x-success app.

````
https://rawgithub.com/josephschmitt/safari-x-success/master/callback.html#
	url=[[selection]]
	&x-success={{tweetbot://}}
````

This will open up Mobile Safari and instantly redirect the browser to the url at the url parameter. However, when you hit the back button to return to the initial page, it'll bounce you back to whatever url scheme is defined in x-success. The only downside to this system is there is no way to close the original page automatically via JavaScript like Chrome does. If anyone has any ideas how to do this, feel free to pull request.