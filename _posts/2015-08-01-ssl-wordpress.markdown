---
layout: post
title:  "How to force WordPress to serve over SSL"
date:   2015-08-01 21:50:41
permalink: /how-force-ssl-for-wordpress/
categories: ['Wordpress Development']
---

It took me a bit of trial and error to get this right for [Gotham Quilts](https://gothamquilts.com) but I finally go it and wanted to share the simple solution. You do *no* need a plugin for this!

Note: This post isn't going to cover setting up your server to do SSL right. It's only about how to make it so that WordPress works and is always served over SSL.

### Step 1: Tell WordPress your site is at https: instead of http:

In the Admin panel, go to Settings > General and update the two URL fields to say "https" instead of "http"

![settings](/images/wp-settings.png)

### Step 2: Tell WordPress to force SSL for logins and the admin panel

Open up your wp-config.php file and add these lines:

    define('FORCE_SSL_ADMIN', true);
    define('FORCE_SSL_LOGIN', true);

### Step 3: Add https rule to .htaccess file

Open you .htacess file and add these lines BEFORE the WordPress section:

    <IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteCond %{HTTPS} !=on
	RewriteCond %{HTTP:X-Forwarded-Proto} !https
	RewriteRule ^(.*)$ https://%{SERVER_NAME}/$1 [L,R=301]
	</IfModule>

It's **very important** that these lines are before the WordPress section that starts with # BEGIN WordPress, so that the url will be forced to SSL before the WordPress rules kick in. And definitely do NOT put those lines between the opening and closing WordPress comments, because your lines get blown away when WordPress changes something in the .htacess file.

# That's it!

Well, unless you're terminating SSL at the load balancer, like I am with Gotham Quilts with an AWS ELB. In that case, you also need Step 4:

#### Step 4: Forward headers

Make sure that the server thinks it's in https if it sees HTTP_X_FORWARDED_PROTO set to https:

	if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https') {
		$_SERVER['HTTPS']='on';
	}