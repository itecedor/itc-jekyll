---
layout: post
title:  "Add structured data to Shopify products with Product Metafields"
date:   2025-06-25
permalink: /shopify-product-metafields/
image: shopify-product-metafield-ui.png
categories: Shopify
---

Shopify's native product fields are probably sufficient for 95% of businesses selling simple products, but for some businesses, the product catalog could benefit from having more structured data defined at the product level.

That's why Shopify introduced [Product Metafields](https://help.shopify.com/en/manual/custom-data/metafields) in 2021, and has been iterating on the feature ever since.

From Shopify's documentation, here are some examples of the type of product data that can be stored in metafields:

* part numbers
* color swatches
* launch dates
* related products
* blog post summaries
* files for download
* lists of ingredient

As I write this in June of 2025, there are [26 different metafield content types available](https://help.shopify.com/en/manual/custom-data/metafields/metafield-definitions/metafield-types). 

For most shops, the most common data types you'll use are probably *text* and *color*.

## Example Product Metafield Setup

Let's say that a store selling clothes wants to display these additional details on each product:

* Country of Origin
* Machine Washable

### Product Metafield with Drop-down Options

For the Country of Origin field, we're obviously storing text, but if you were to allow users to type into a free-form text field, you'll end up with messy duplicates like "USA" vs "United States" versus "US". So instead of a plain text field, you'll want to set up a drop-down field with a predefined set of options for to user to choose from.

To open the Metafield definitions screen, click on Settings>Metafields and metaobjects>Products, which will take you to a list of all existing Product Metafields. If you haven't yet made any, it'll look like this:

<img src="{{ site.baseurl }}/assets/image/empty-shopify-metafields.png" width="840" height="326" alt="Empty list of Shopify Product Metafields">

Click "Add definition" and enter the text you want displayed in the Product admin for this field, in this case, "Country of Origin". You can add text in the "Description" field if you'd like but it's not required.

<img src="{{ site.baseurl }}/assets/image/create-product-metafield.png" width="840" height="326" alt="Product Metafield Form">

Then click "Select type" to open the field data type options drop down:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-data-types.png" width="840" height="326" alt="Shopify Product Metafield Data Type Drop Down">

In this case, we'll choose "Single Line Text", since the values will always be short (ie country names). If we needed to store longer text, we'd choose "Multi-line text", or to store numbers, choose Integer or Decimal, etc.

Once you've clicked "Single Line Text", the form will update with that selection and two new options, "One value" or "List of values":

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-one-value-list-values.png" width="840" height="326" alt="Shopify Product Metafield One Value vs List of Values">

The wording on these two options maybe could be clearer, but essentially these two options mean "allow the user to enter one piece of text" vs "allow the user to enter a list of text". In other words, do you want the field to store text like "USA" for a Country of Origin field, or text like "Milk, Sugar, Butter" for a field that stores a list of ingredients.

Once you choose "One value", some more options appear below:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-single-line-text-options.png" width="840" height="326" alt="Shopify Product Metafield Single Line One Value Options">

All of these additional options are optional, but in our case, we'll be choosing "Limit to preset choices" in order to create our drop down menu of countries for the uer to choose from. Once you've checked that checkbox, a field appears to allow you to enter the options:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-drop-down-options.png" width="840" height="326" alt="Shopify Product Metafield Single Line One Value Options">

Type all the options you want to have in this field, click save, and you're done!

In the Admin, the product will now display this new field in the Product metafields section, and clicking into the field will display the drop down with the options you set up:

<img src="{{ site.baseurl }}/assets/image/shopify-product-metafield-dropdown.png" width="840" height="326" alt="Shopify Product Metafield with Drop Down Options">

### Product Metafield with True/False Values

In the case of the "Machine Washable" field, the only valid options are "Yes" and "No", which in programmer-speak is a boolean value -- the only acceptable options are True ("Yes") and False ("No"). 

Shopify shows this data type as "True or false" in the "Select type" drop down, because they are trying to be friendly to non-developers, but if you type "boolean" into the search, it understands what you are looking for:

<img src="{{ site.baseurl }}/assets/image/shopify-metafield-true-false-field.png" width="840" height="326" alt="Shopify Product Metafield with true/false values">

Since this is a much simpler type of field with only two valid options, there are no additional configuration options after choosing it from the drop down, you can just click Save after choosing it.

Now on the Product admin screen, the new Metafield is displayed and when you click into it, the options True and False are displayed as radio buttons, allowing only one selection to be made:

<img src="{{ site.baseurl }}/assets/image/shopify-product-metafield-true-false.png" width="840" height="326" alt="Shopify true/false Metafield in Product Admin">