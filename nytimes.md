# Browser Refresh Button allows Reading without Paywall

This was originally discovered sometime in early 2019. Emailed the times, never heard anything back, and resubmitted to HackerOne on 2/15/21.

## Summary:

All paywalled NYTimes content (besides nytimes games) are trivially accessed by pressing the cancel/refresh button at the right time in all modern browsers.

## Steps To Reproduce:

1. Select a browser of your choice - I've tested this on chrome, Firefox, and safari.
2. Don't log in to a New York Times account, and access a page that is behind a paywall. For example, click articles until the limit is reached, or grab something from NYTimes Food, like the following link: https://cooking.nytimes.com/guides/48-how-to-make-chili
3. Notice how if you don't do anything, the page content loads, then the ads and paywall load.
4. Look for the refresh button in your browser. It should be to the left or right of the search bar.
5. Click the refresh button, and click it around when the text content of the site is loading. With timing done correctly, the paywall (and ads) will not load, and the user will have unfettered access to the page that requires a paywall. This might refreshes initially to get the timing right, but is fairly simple for a non tech-savvy user to perform once they know the trick.

## Supporting Material/References:
Attached is a gif of getting past the NYTimes Food paywall. It's tough to see, but I click twice on the refresh button. Once to begin the page load, and one more to interrupt before the paywall is loaded.

## Deeper Explanation for Non Technical Readers:
To understand how to fix this bug, let's dive a bit deeper. When someone's browser loads a web page, there is a back and forth (described in more depth here - https://en.wikipedia.org/wiki/Transmission_Control_Protocol). As page content loads, the New York Times web servers synchronize with the browser. When a user presses the refresh/cancel button, they are forcing this synchronization to stop, before ads and the paywall are loaded.

## Recommendations:
Reverse the order of loads to load the paywall before page content and ads. It is important to keep the ads last, as pictures take a while to load, and doing this first will result in a slower web page compared to competitors. On the other hand, the paywall should be (or can be made to be) fast, and loading this before the page content should increase security without decreasing usability.



# Impact:

This vulnerability is relatively easy to discover, and non-technical people can learn to use it quite easily. The bug is present in all browsers, and users only need to click twice in the same spot to get it to work. That being said, it is also not high severity - no sensitive information is leaked from NYTimes.

That being said, this is dangerous to the company's bottom line. To test this, I've showed this vulnerability to a few non technical friends. They now frequently read the times online, but are not subscribed. It is very likely that I am not the only person who has discovered this bug, because there is enough visible delay to realize that the page content is loaded before ads and the paywall. It's asking to be discovered and more broadly used, even though the fix for this is trivial.