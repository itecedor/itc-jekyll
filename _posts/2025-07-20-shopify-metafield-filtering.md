---
layout: post
title:  "Use Shopify Product Metafield Data for Filters in Theme"
date:   2025-07-20
permalink: /shopify-product-metafields-frontend-filters/
image: shopify-product-metafield-ui.png
categories: Shopify
---

In a recent Shopify project, I set up custom Product Metafields to store additional product information, and then exposed them in the theme so that customers could filter results by those metafield values.

It wasn't as straight-forward as I expected, so I'm writting up this tutorial to show the steps to achieve this.

## Set Up Product Metafields

<a href="{{ site.baseurl }}/shopify-product-metafields">Create your Product Metafield</a> in whatever configuration you need to store your data. Then, check off the "Use as a filter" option at the bottom of the Metafield definition form:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-filter-option.png" width="840" height="326" alt="Shopify Metafield Filter Option">

Once you have your Metafield set up, go into your products and update them to add values into this field.

The <a href="https://help.shopify.com/en/manual/shopify-admin/productivity-tools/bulk-editing" target="_blank">Shopify Product Bulk Update feature</a> is really handy for this, just remember to expose the metafield by clicking the "Columns" button at the top right so you can see the field!

## Install Search & Discovery App

If you don't already have it installed in your shop, install the <a href="https://apps.shopify.com/search-and-discovery" target="_blank">free Shopify Search & Discovery App</a>. Then open the App and click on Filters:

<img src="{{ site.baseurl }}/assets/image/shopify-search-discovery-filters.png" width="840" height="326" alt="Shopify Search & Discovery App Filters Screen">

Click "Add filter" at the top to open the form to create a new filter, then click "Select source", which will open up a new modal:

<img src="{{ site.baseurl }}/assets/image/shopify-filter-modal.png" width="840" height="326" alt="Shopify Search & Discovery Add Filter Source Modal">

Each row in this modal is a piece of structured data in your store that can be used for filtering. Find your Metafield in this list and select it. 

For this example, I am using the "Country of Origin" field, which is a single-line text field with a pre-defined list of 3 options to choose from. Once you select the Metafield you want to use, the form will update showing the existing *values* of that field:

<img src="{{ site.baseurl }}/assets/image/shopify-search-filter-dropdown.png" width="840" height="326" alt="Shopify Search & Discovery Filter for Drop Down Metafield">

Once you click Save, this new filter will be displayed in your list of filters:

<img src="{{ site.baseurl }}/assets/image/shopify-search-discovery-filters-list.png" width="840" height="326" alt="Shopify Search & Discovery Filter List">

## That's it, You Now Have a Metafield Filter!

After saving your filter, when you go to your website and view a collection whose products have values in this new Metafield, you'll now see a new filter in the filters area:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-filter-theme.png" width="840" height="326" alt="Shopify Metafield Filter on Horizon Theme">

The above screenshot is using the <a href="https://themes.shopify.com/collections/horizon-themes" target="_blank">Horizon theme</a> without any customization.

<img src="{{ site.baseurl }}/assets/image/dawn-theme-filters.png" width="840" height="326" alt="Shopify Metafield Filter on Dawn Theme">

And here's a screenshot of the same data displayed in the <a href="https://themes.shopify.com/themes/dawn/presets/dawn" target="_blank">Dawn theme</a> without any customizations.
