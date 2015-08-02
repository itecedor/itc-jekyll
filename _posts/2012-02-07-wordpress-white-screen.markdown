---
layout: post
title:  "Upgraded WordPress, and now wp-admin is a blank white screen? Here’s the fix."
date:   2012-02-07
permalink: /upgraded-wordpress-and-now-wp-admin-is-a-blank-white-screen-heres-the-fix/
categories: ['WordPress development']
---

<img src="{{ site.baseurl }}/images/white-screen.png" class="post-thumb alignleft">So just now, I upgraded the last of my properties to the latest WordPress release, 3.3.1. I usually wait to do the most important one until after I’ve done all the others, to make sure that the one that brings in the dough doesn’t get killed by an errant upgrade. Usually I have nothing to worry about, as WordPress does such a fantastic job of upgrading smoothly with just one click, but every so often, well . . .

###Every so often, things break.

Today was one of those “every so often” times, and instead of the “What’s new in this version” admin screen I expected, I was greeted with a horrifying white screen, completely empty of content. I immediately checked the user-facing part of the site, and that looked fine, so I was confused. I’ve never seen a blank page instead of an admin panel, which is wacky enough, but having that while the user-facing section of the site is functional? Inconceivable! (Princess Bride anyone?)

###Trying anything I can think of

A quick Google [led me to try something that didn’t make any difference](http://bavotasan.com/2008/the-wordpress-admin-panel-and-the-blank-screen-of-death/).

My next step was to turn on WP_DEBUG to see what errors came up, and the first one said “load_plugin_textdomain was called with an argument that is deprecated since version 2.7 with no alternative available” — so clearly something else installed on WP was no longer compatible with the new version. Now I at least knew what I was dealing with, it must be a bad plugin.

And no, of course I hadn’t turned off all plugins in order to upgrade, who actually does that? Admit it, you don’t either. And I’m sure you don’t back up your DB before-hand, either (neither do I).

So, the next step was obvious: Turn everything “extra” off and, assuming that brought my admin panel back from death, then start turning them back on one at a time to figure out what was breaking the site.

###Turning off all plugins without an Admin panel

To get rid of all plugins, I went into my FTP client and dragged all plugin folders into the wp-content folder. This makes their files inaccessible to WordPress and essentially uninstalls them. Depending on what plugins you had, you may get additional errors after doing this step, and you’ll need to deal with those (for example, cachine plugins often add additional PHP files to wp-content, and those will need to be deleted through the FTP client).

When I refreshed wp-admin, the admin panel popped up! Score!

Time to turn the plugins back on one at a time, until the site breaks again, in order to find . . .

###The Culprit

The cuplrit? [Popup Domination](http://www.popupdomination.com/). The plugin we all love yet hate. With the website that makes GoDaddy seem friendly and streamlined . . . figures.

I found [this post in their support section](http://getsatisfaction.com/popdom/topics/popup_domination_2_5_6_has_no_updates_to_wp_3_3_1) saying that an updated version of the plugin is available that IS compatible with 331, so I’ve emailed them to get a copy.

Sure woulda been nice for them to **proactively mail their customers letting them know** . . . hint hint Popup Domination. Free services give better customer service.