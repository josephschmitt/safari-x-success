# Safari X-Success

This is an empty shell page with some JavaScript in it that allows Mobile Safari on iOS to mimic Chrome on iOS's x-success back button behavior. It is based on [Greg Pierce's post](http://agiletortoise.com/blog/2014/02/28/mimic-x-callback-url-in-mobile-safari/) to do the same with iframes. This solution uses the JavaScript history API instead of an iframe, which feels a bit cleaner to me.

## Usage

The URL scheme is very similar to Greg's post, with two small differences: 

1. The URL itself points to the callback.html page in this repository directly. This is for a combination of laziness and security; you can see the source code on Github and trust I'm not stealing your browser sessions :-).
2. Use a hash (#) instead of query parameter (?) for the parameters. This is so that Safari treats all of the pages with different parameters as a single page, and will just re-load the page if it's already open in your browser instead of opening up a new page. This means you'll only ever have at most one x-success browser window open instead of a bunch. This should help mitigate the problem with not being able to close the window when jumping back to the x-success app.

````
https://rawgithub.com/josephschmitt/safari-x-success/master/callback.html#
	url={{http://your-url.com}}
	&x-success={{tweetbot://}}
	&x-source={{Source Friendly Name}} //this is optional. If submitted it will show up as the page name.
````

Here's a live example that opens [MacStories](http://macstories.net) and then Tweetbot if you go back.

````
https://rawgithub.com/josephschmitt/safari-x-success/master/callback.html#url=http://macstories.net&x-success=tweetbot://&x-source=Tweetbot
````

This will open up Mobile Safari and instantly redirect the browser to the url at the url parameter. Then, if you hit the back button to return to the initial page, it'll bounce you back to whatever url scheme is defined in x-success. Quick tip: did you navigate a few pages but now want to quickly return to the x-success page? Tap-and-hold on the back arrow in Safari and you'll see the page at the bottom of the list. If you submitted the x-source parameter, the page will even use it as its name.

~~The only downside to this system is there is no way to close the original page automatically via JavaScript like Chrome does. If anyone has any ideas how to do this, feel free to pull request.~~ This issue has been somewhat addressed by switching to using hash instead of question mark for the parameters separator. Now, if you alrady have the callback page open in Safari, Safari will not open a new window, it'll re-use the same one.