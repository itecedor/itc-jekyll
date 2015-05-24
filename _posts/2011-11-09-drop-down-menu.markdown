---
layout: post
title:  "How to use a drop-down menu for WordPress custom fields"
date:   2011-11-09
permalink: /how-to-use-a-drop-down-menu-for-wordpress-custom-fields/
categories: ['WordPress development']
---

Most of my programming time right now is devoted to getting Snail a Note launched as soon as possible. I’m building on top of WordPress because WP’s default features are so powerful that they lend themselves easily to managing the “notes” I need to deal with for Snail.

Anyone who’s done WP custom work probably already knows how to create a custom post type or add custom fields, but have you ever tried to make your custom field look and work like a drop-down menu instead of a fill-in form? I bet you haven’t (or at least haven’t written about it!), because I googled fruitlessly looking for a tutorial on how to do just that!

Now that I have it working on my site, I’m writing the instructions up so that the next person who wants this can do it more quickly than I did for this project ;o)

###Why a drop-down menu?

For my project I knew that I needed a way to control the value of the “note status” field in order to keep our “Snails” from using crazy statuses that would get lost in the shuffle or lead to confusion. My partner and I sat down and defined 4 official statuses (“blank” is the starting status even though as a programmer that really rubs me the wrong way!) that apply to each note as it goes through its lifespan, and I needed to programmatically force the fulfillment team to always use those statuses and nothing else. The solution is a drop-down menu that has only the approved choices in it.

###How to make the post meta field into a drop-down menu

After you’ve created the custom field you want to use (there are tons of tutorials out there for how to do this, so I won’t cover that here), go to where that code is (in your theme’s functions.php file or in your plugin). These changes will happen right in your custom fields code.

The first step is to change the field in the post meta section into a drop-down menu. The code for this lives inside the add_meta_box() function and lists the custom fields you’ve defined. It looks something like this:

<pre>
function custom_meta_options() {
    global $post;  
	$custom = get_post_custom($post->ID);  
	$field= $custom["field"][0];  
	?>  
	Field:<input name="field" value="<?php echo $field; ?>" />  
}
</pre>

The code above would give you a field like this:

<img src="/images/field.png" style="width:200px">

This is the default way to add a custom field, and it allows the end-user to type whatever they want into that new field type.

To change this field into a drop-down menu is as simple as changing the HTML as if it were a basic form:

<pre>
function custom_meta_options(){
	global $post;
	$custom = get_post_custom($post->ID);
	$field= $custom["field"][0];
	?>
	<strong><label>Field:</label></strong>
	< select name="field">
		< option value=""></option>
		< option value="Draft">Draft</option>
		< option value="Scheduled">Scheduled</option>
		< option value="Mailed">Mailed</option>
	< /select>
</pre>

Now, you have a drop-down field, like this:

<img src="/images/selected-dropdown.png" style="width:200px">

Pretty awesome, huh?

There’s one more thing you should do:

###How to pre-select the current value

If you leave the drop-down field as above, the user will not be able to tell what the current value of that field is. So you should be checking that and returning it to the user with a quick if statement, like this:

<pre>
	< ?php if(isset($field)): ?>
		< option value="<?php echo $field; ?>" /><?php echo $field; ?></option>
</pre>

And again, that’s it. I was very excited to see it working so easily once I finished!