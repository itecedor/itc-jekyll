---
layout: post
title:  "How to force Facebook to re-scrape your URL"
date:   2012-04-11
permalink: /how-to-force-facebook-to-re-scrape-your-url/
categories: ['Facebook marketing']
---

<img src="{{ site.baseurl }}/images/empty-300x171.png" class="post-thumb alignleft">Have you ever gone to post an update on Facebook and linked to a page on your site, only to find that Facebook wasn’t pulling in the latest version of that URL? It’s really frustrating to have content you want to promote and see an empty link in the wall update!

The reason this happens is because FB caches **everything**, or maybe more accurately, SUPER CACHES EVERYTHING. It’s impressive from a technical standpoint and makes sense for performance and all that, but it definitely sucks if you’re a user trying to market something you recently changed.

###So what’s the solution?

Use Facebook’s own tool to clear their cache!

One of the best Facebook dev tools is the [Debugger](https://developers.facebook.com/tools/debug) (also called the “linter”), which is intended to help you see how your Facebook-specific meta tags are going to look when the page is shared on FB.

If you go to the debugger and drop in the URL you’re having trouble with, Facebook will actually reach out to your URL **right then** and grab the current content to display the debugger results.

Doing this also **clears Facebook’s cache of your page instantly**
. Seriously!

After you lint your URL, you can immediately go back and type your update in again, and the good stuff will show up. It’s that easy!

For the update above, this is what the debugger showed:

![result](/images/result.png)

Which is, of course, the content I was trying to share.

Immediately going back to my Facebook page and trying the update again (you should refresh the page before you start just to make sure it will actually grab the URL) yielded this:

![good status](/images/goodstatus.png)

That’s more like it!

It’s really that easy, and I’m so glad I thought to try this. Hope it helps some of you out there too!

###Oh and bonus:

If you’re in QA and want to test what will happen when you share content on FB but can’t actually POST the content to FB because it’s still in development, the debugger is the way to go for that too.

###And one last thing:

If you’re a knitter reading this and want to actually go to the content in the screenshots above, check out the [Koigu KPPPM yarn](http://chiagu.com/collections/yarn/products/koigu-kpppm-yarn) for sale in my knitting online store!