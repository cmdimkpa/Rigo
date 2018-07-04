![rigo_logo](http://ceres-ai.com:6765/static/logo-rigo.jpg)
# Rigo
A lightweight database for Python Applications
<br>
![rigo_logo](http://ceres-ai.com:6765/static/logo-rigo.jpg)<br>

RigoDB is a simple, functional, and powerful local database solution for Python applications. Many applications simply require effective persistence and fast I/O in a database -- and RigoDB delivers high performance in this regard.

## Getting Started

First, you should install Rigo from pip:

<pre>
  pip2 install --upgrade rigo
  </pre>
  
Then, in your Python2 code, import Rigo:

<pre>
  from rigo import *
  </pre>
  
You are now ready to start working with databases. Let's take a quick tour of Rigo's functionality:

## Create a Database

To create a database, use the following syntax:

<pre>
  >>> RigoDB("new_database",{"dbname" : "sample_database","dbpassword" : "sample_password"});

'CreateDBSuccess: database: SAMPLE_DATABASE was created'

  </pre>

## Add a Table

To add a table to your database, use the following syntax:

<pre>
>>> RigoDB("add_table",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table"});

'CreateTableSuccess: table: SAMPLE_TABLE was created'
</pre>

## Add some data to a Table

To add some data to your table, use the following syntax:

<pre>
>>> RigoDB("new_entry",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entry":{"a":"apple"}});

'WriteTableSuccess: table: SAMPLE_TABLE  was updated'
</pre>
<pre>
>>> RigoDB("new_entry",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entry":{"b":"bee"}});

'WriteTableSuccess: table: SAMPLE_TABLE  was updated'
</pre>
<pre>
>>> RigoDB("new_entry",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entry":{"c":"cat"}});

'WriteTableSuccess: table: SAMPLE_TABLE  was updated'
</pre>

## View a Table

You can view a whole table or a list of specific rows. To view the entire table, set the `entryPos` parameter to `'*'`. To view a selection, set to a list of row numbers e.g. `[0,3,4]` for the first, fourth and fifth rows. Note: Rigo is zero-indexed. 

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":"*"});

[{'a': 'apple'}, {'b': 'bee'}, {'c': 'cat'}]

</pre>

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":[0,2]});

[{'a': 'apple'}, {'c': 'cat'}]

</pre>

## Modify a Table (edit & delete rows)

To modify a table, you modify a specific row:

<pre>
>>> RigoDB("edit_entry",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":1,"new":{"b":"baloon"}});


'EditTableSuccess: table: SAMPLE_TABLE was updated at row: 1'
</pre>

Let's check if there are changes by viewing the entire table again:

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":"*"});


[{'a': 'apple'}, {'b': 'baloon'}, {'c': 'cat'}]


</pre>

The second entry has indeed changed, as intended.

You can also delete a specific entry:

<pre>
>>> RigoDB("delete_entry",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":2});

'EditTableSuccess: row: 2 of table: SAMPLE_TABLE was deleted'

</pre>

Let's check:

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":"*"});

[{'a': 'apple'}, {'b': 'baloon'}]
</pre>

Alright.

## Delete a Table

To delete a Rigo table, use the following syntax:

<pre>
>>> RigoDB("delete_table",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table"});

'DeleteTableSuccess: table: SAMPLE_TABLE was deleted'

</pre>

Let's check:

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":"*"});

'TableAccessError: table not found'

</pre>

## Delete a Database

To delete a Rigo database, use the following syntax:

<pre>
>>> RigoDB("delete_database",{"dbname" : "sample_database","dbpassword" : "sample_password"});

'DBOpSuccess: database SAMPLE_DATABASE was deleted'

</pre>

Let's check:

<pre>
>>> RigoDB("view_entries",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table","entryPos":"*"});

'DBAccessError: could not connect to database [not found]'

</pre>

## Remote Storage Options: Rigo Web API

The Rigo Web API allows you to use Rigo over HTTP. This way, other non-Python web and mobile applications can use the same database. Coming soon.

## Rigo Performance Tests

Watch this space. Coming soon.
