---
layout: post
title:  "How to disable WooCommerce Restock refunded items unchecked"
date:   2018-04-30 15:50:41
permalink: /how-to-disable-woocommerce-restock-refunded/
categories: ['WooCommerce Customization']
---

WooCommerce has so many features and settings, I'm always surprised to find that something is NOT customizable when I run into problems running [Gotham Quilts](https://gothamquilts.com).

This time, what I needed was a way to default the "Restock refunded items" checkbox in the WC order admin screen to UNCHECKED:

![restock refunded items](/images/restock-refunded-items.png)

Our primary use case for refunding a line item in an order is because we had the item listed as in stock online, but when we went to fill the order discovered we did not have it. Because this checkbox is CHECKED by default, we've accidentally INCREASED the stock level of the item at the time of the refund! It's even resulted in multiple sales of the same out-of-stock item by accident... *facepalm*

After a lot of googling and digging into the [WooCommerce Github repo](https://github.com/woocommerce/woocommerce/) I was convinced that there's no setting I could use to do what I needed, so I hacked it by adding a line of Javascript to the WP admin.

It's not pretty, but it works!

If you too want your restock refunded items checkbox disabled, add this to your theme's functions.php file:

    add_action('admin_footer', 'uncheck_restock_refund_checkbox');
    function uncheck_restock_refund_checkbox() {
    	echo '<script>jQuery("#restock_refunded_items").prop("checked", false);</script>';
    }

I'm also planning to implement a setting flag for this to core and contribute a patch back up to them, but who knows if they'll approve it?

--

* Update March 2019: [They implemented my suggestion and PR!](https://github.com/woocommerce/woocommerce/pull/21314)

* Update April 2019: When looking to update this blog post, I discovered that the merged PR has subsequently been broken... the newly-created config is no longer in the repo, but the code that USES that config is. D'oh! Looking through the commit history, the commit isn't there at all in the config file, so it looks like a potential force push problem... [I've opened a new issue](https://github.com/woocommerce/woocommerce/issues/23419) and am waiting to hear if they want me to open a new PR or what.
