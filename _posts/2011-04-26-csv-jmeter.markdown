---
layout: post
title:  "How to use a CSV file with JMeter"
date:   2011-04-26
permalink: /how-to-use-a-csv-file-with-jmeter/
categories: ['Web development']
---

I’m testing a new site right now and part of my process required load testing of the “add to cart” functionality. To do this, I wanted to have multiple “users” all on the system at the same time, each adding the same item to their cart.

JMeter seemed like the logical way to deal with this, but figuring out how to get it to handle various usernames and passwords wasn’t that easy.

After some trial and error and a bunch of Googling I have it working, so thought I’d do a quick post on it for others to reference:

First, create a CSV file with the logins and passwords. You can just do this in a text editor, and the format should be:

username,password
username2,password2
username3,password3

Save that file in the bin directory where your JMeter installation lives. For this example, I saved the file as “logins.csv”.

Now go into JMeter and find the HTTP request step that you want to modify to use the values in this CSV file. Right click on it and go to Add > Config Element > CSV Data Set Config. This adds the CSV Data Set Config as a child of the HTTP request.

![first](/images/csv1.png)

In the tree above, you can see that I’m using the CSV data to modify the “Log in” HTTP Request.

Now click on the CSV Data Set Config step to modify it. Its screen looks like this:

![second](/images/csv2.png)

You’ll need to fill in at least 3 values on this screen:

* Filename: if your file is in the /bin directory, this can be just the filename. If it’s somewhere else, use the full path to the file.
* Variable names: this is the equivalent to a “column name” in a spreadsheet.
* Delimiter: comma is the default delimiter, but if your file uses tabs this is the place to say so.

The other fields are optional but may be useful to you. Read all about them on the [JMeter CSV Data Set Config user manual](http://jakarta.apache.org/jmeter/usermanual/component_reference.html#CSV_Data_Set_Config).

After the CSV step is filled out correctly, go back to your HTTP request and change the value of the login and password fields to variables.

Here’s what that looks like in my test:

![third](/images/csv3.png)

Because I had defined my variables as “login” and “password” in the previous step, in this step I need to use those variables as the value of the parameters that are being sent with the request. To do that I replaced the email address with ${login} and the password with ${password}.

Now when you run this test, JMeter will fill in the values of those two variables with what’s in the CSV file. The first thread will use row 1, the second thread uses row 2, etc etc.