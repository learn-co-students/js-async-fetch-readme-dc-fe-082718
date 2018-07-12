Fetching Asynchronously with JavaScript
---

## Problem Statement

When it comes to making engaging web sites, we often find ourselves needing to
send a lot of data (text, images, media, etc.). But sending and loading this
data on page visit *feels* slow, especially on a slow connection.

However, web users expect sites to load quickly and to stay updated. Research
shows that 40 percent of visitors to a website will leave if the site takes
more than 3 seconds to load. Mobile users are even less patient.

We deliver sites that don't bore users by using a technique called ***AJAX***.
In AJAX we:

1. Deliver an initial, engaging page using HTML and CSS
2. Use JavaScript to add more to the DOM, behind the scenes

In this lesson, we will use the JavaScript `fetch()` function and experience
the AJAX technique.

## Objectives

1. Explain how to fetch data with `fetch()`
2. Working around backwards compatibility issues
3. Identify examples of the AJAX technique on popular web sites

## Explain How To Fetch Data With `fetch()`

The `fetch()` function retrieves data. It's a global function.

Here's the skeleton for using it:

```js
fetch("string representing a URL to a data source")
  .then(response => response.json())
  .then(json => ...)
```

The first thing you need is a `String` that represents a URL that can provide
you some data. As it happens, http://api.open-notify.org/astros.json will
provide a list of the humans in space. You can paste this URL into a browser
tab and see that this URL returns a JSON structure. You provide this string as
the first argument to `fetch()`.

You will want to _chain_ a call to `then()` at the end of `fetch()`.

> **REMEMBER**: Since JavaScript doesn't care about whitespace
> 
> ```js
> fetch("string representing a URL to a data source").then(response => response.json());
> ```
> 
> is the same as:
> 
> ```js
> fetch("string representing a URL to a data source")
>   .then(response => response.json());
> ```

The `then()` takes a function. Here is where you tell JavaScript to ask the
network response to be turned into JSON.  When starting out, this first
`then()` will pretty much be the same across all your uses of `fetch()`.

The final `then()` is when you actually get some JSON passed in. You can then
do something with the JSON. The easiest thing is to `console.log()` the JSON
_or_ to hand the JSON off to another function.

```js
fetch('http://api.open-notify.org/astros.json')
  .then(response => response.json())
  .then(json => console.log(json));
```

![kimmy wow](http://i.giphy.com/3osxYwZm9WZwnt1Zja.gif)

## Working Around Backwards Compatibility Issues

As you can see, `fetch()` provides us with a clean, low-maintenance way to get
and work with resources. However, `fetch()` has only recently arrived in
browsers. While it's _generally_ safe enough to lean on, other in historical
code,  you might see `jquery.ajax` or `$.ajax` or an object called an
`XMLHttpRequestObject`.

## Identify Examples Of The AJAX Technique On Popular Web Sites

The AJAX technique opens up a lot of uses!

* It allows us to pull in dynamic content. The same "framing" HTML page remains
  on screen for a cooking website. The recipe on display updates without page
  load.  This approach was pioneered by GMail whose navigational area is swapped
  for mail content swiftly thanks to AJAX.
* It allows us to get data from multiple sources. We could make a website that
  displays the current weather forecast and the current price of bitcoin side
  by side! This approach is used by most sites to render ads. Your content loads
  while JavaScript gets the ad to show and injects it into your page.

## Conclusion

Modern websites now often have just _one_ HTML page, which loads initially. As
you navigate around one of these sites, instead of jumping from HTML page to
HTML page, JavaScript is loading the exact content we need and swapping it in
when its ready. Using `fetch()`, we can easily include requests for data wherever
we need to in our code. We can `fetch()` data on the click of a button or the
expansion of a tab, instead of when the page initially loads.

By doing this, we can send _only_ the data that is needed, saving on server
bandwidth while minimizing loading times for the end user. The `fetch()` method
opens the world of third party data which we can use in our own projects.

## Resources

- [MDN Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [HTML5 Rocks Promises](http://www.html5rocks.com/en/tutorials/es6/promises/)

<p class='util--hide'>View <a href='https://learn.co/lessons/javascript-fetch'>Getting Data from the Web</a> on Learn.co and start learning to code for free.</p>

[space]: https://www.warnerbros.com/archive/spacejam/movie/jam.htm
