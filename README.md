# getTweet
#### A bit of jQuery for loading a user's latest tweet(s) without the Twitter API

### Usage:
To get the tweet run `getTweet.please(widget, howMany, name, callback);`. Where `widget` is the Twitter widget ID number, `callback` is the function to execute after the tweet has been fetched, `howMany` is an optional number 1-20 (designating how many tweets to load - default is one), and `name` is an optional name for the timeline. Once that's been run, the tweet will be publicly available as an object at `getTweet.tweet`. It will look like this:

```javascript
getTweet.tweet = {
  html: "string", // HTML from the tweet 
  link: "https://twitter.com/user/statuses/[...]", // Permalink to tweet
  name: "Full Name", // Full name of user
  pic:  "https://si0.twimg.com/profile_images/[...]_normal.jpeg", // URL for user's profile picture
  text: "string", // Text from tweet (no links)
  time: 1371501240000, // Number of milliseconds since January 1, 1970, 00:00:00 UTC
  user: "@user" // User's screen name
}
```

If `howMany` is a number specified between 2 and 20, an array (`getTweet.tweets`) will be returned in addition to `getTweet.tweet` (which will only contain the latest tweet). `getTweet.tweets` will be an array of objects structured just like the one above, with `getTweet.tweets[0]` being the most recent. Since 20 is the maximum number of tweets available, if a number greater than that is entered, only the latest tweet will be returned.

If a string is included for `name` the `tweet`/`tweets` object will be returned at `getTweet[name].tweet`(s) instead of `getTweet.tweet`(s). The `name` parameter is required if you want to access multiple widgets.

### Help:
You can get any twitter user's ID number by creating a [Twitter widget](https://twitter.com/settings/widgets). Type in the desired username in the configuration settings and click the blue "Create Widget" button. The widget's ID number will be in the `data-widget-id` attribute of the `<a>` in the generated code.

### Dependancies:
  - jQuery
