---
layout: post
title:  "MongoDB cheat sheet"
date:   2011-11-07
permalink: /mongodb-cheat-sheet/
categories: ['Mongodb']
---

I find myself referring back to these MongoDB commands all the time so figured others would too:

####Navigating

Show full list of databases:  `show dbs;`  
Change to another db: `use [dbname];`

####Querying:

Basic count: `db.[collection].count({QUERY});`  
Output find with nice formatting: `db.[collection].findOne({QUERY});`  
Find distinct values for X: `db.[collection].distinct(X, {QUERY});`  

####Find and Update Data:

Update one record: `db.[collection].update({QUERY}, {$set: {UPDATE_QUERY}});`  
Update all records that fit the criteria:
 `db.[collection].update({QUERY}, {$set: {UPDATE_QUERY}}, false, true);`  

**Note**: The shell won’t give you a count of how many records were updated, so always do a count() on the query first to make sure the results are what you want!

###Deleting and removing (in order from smallest to largest operation):

Remove records from a collection: `db.[collection].remove({QUERY});`  
Remove an entire collection: `db.[collection].drop();`  
Fully delete a database:  
 `use [dbname];`  
 `db.dropDatabase();`

**Note on the above**: When you do `db.[collection].drop()`, the contents of that collection are removed but the physical space devoted to the collection is not released. If you were to check the size of your DB before and after the drop(), you would see that the size remains the same. In other words, after drop(), you have a bunch of empty space devoted to the old collection.

So, if you’re trying to free up room because you’ve run out, you need to do `db.dropDatabase()` instead to reclaim that space on the server.

###Show operations:

Show all current operations/queries/syncs: `db.currentOp();`