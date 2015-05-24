---
layout: post
title:  "Optimizing WordPress Workflow"
date:   2013-04-04
permalink: /optimizing-wordpress-workflow/
categories: ['web development']
---

After years of blogging on WordPress and building dozens of client sites on it, I’ve come to prefer my own modified version of a WordPress install.

For example, I always put WP in its own directory and never create a user with the username “admin.” While in development, I like to lock the staging environment with basic HTTP authentication.

To make my workflow easier, I have these basic changes in a git repo, and simply check it out when I go to install WordPress.

I’ve now put that repo up on Github as a public repo called [hardened-wp](https://github.com/itecedor/hardened-wp). Please feel free to use it on your own projects! I hope it’ll save you time and aggravation in the future.