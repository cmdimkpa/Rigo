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

<pre>
  >>> RigoDB("new_database",{"dbname" : "sample_database","dbpassword" : "sample_password"});

'CreateDBSuccess: database: SAMPLE_DATABASE was created'

  </pre>

## Add a Table

<pre>
>>> RigoDB("add_table",{"dbname" : "sample_database","dbpassword" : "sample_password","tablename":"sample_table"});

'CreateTableSuccess: table: SAMPLE_TABLE was created'
</pre>

## Add some data to a Table

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

## Modify a Table

## Delete a Table

## Delete a Database

## Remote Storage Options

## Rigo Performance Tests
