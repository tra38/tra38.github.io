---
title_bar: Technical - SQL Ordinals and Variables
post_title: Making Your SQL Easier To Type and Read 
post_subtitle: Ordinals and Aliases
layout: default
---
Writing SQL can be a painful experience. But there are two shortcuts that can be used to make your code easier to type. Both shortcuts are cool to understand, but only one is actually advised by the broader "SQL community".

I was inspired to write this blog post while completing Codecademy's tutorial "SQL: Analyzing Business Metrics". In one exercise in the tutorial, I had to write an SQL query to find out how many people are playing a game per day. This was the query I wrote:

{% highlight psql %}
SELECT date(created_at), count(DISTINCT user_id)
from gameplays
GROUP BY date(created_at)
ORDER BY date(created_at);
{% endhighlight %}

And this is the resulting table...
{% highlight sql %}
date(created_at)	count(distinct user_id)
2015-08-04			99
2015-08-05			117
2015-08-06			106
...
{% endhighlight %}

But the SQL query is too verbose and unclear. Could there be a simpler way to refer back to 'date(created_at)'? Codecademy suggest using "ordinals". Ordinals are numbers that are used to refer to the columns you are 'selecting' in an SQL query.

Here's an easy diagram to determine the ordinal number of a SELECT query...
{% highlight psql %}
SELECT date(created_at), count(DISTINCT user_id)
       ^^^^				 ^^^
       1                 2

{% endhighlight %}

By using ordinals, we can simplify our original SQL query as follows:
{% highlight psql %}
SELECT date(created_at), count(DISTINCT user_id)
FROM gameplays
GROUP BY 1
ORDER BY 1;
{% endhighlight %}

This approach *seems* less verbose, but it is actually much more unclear. At first glance, it is impossible to know what "1" is supposed to mean. And if someone decides to switch the order of the SELECT query (putting "count(DISTINCT user_id)" first), the resulting table will be messed up.

There has to be a better way.

And there is. SQL Aliases. Aliases work the same as variables in other programming languages, and to define an alias in SQL, you simply write "AS [alias_name]". Aliases ensure that your SQL code will be self-documenting, while also ensuring that your code would be less verbose.

Here's an example of me defining aliases in an SELECT query, and then using them later on:
{% highlight psql %}
SELECT date(created_at) AS time, count(DISTINCT user_id) AS daily_users
FROM gameplays
GROUP BY time
ORDER BY time;
{% endhighlight %}

An interesting side note is that by defining variables in the SELECT query, you also change the name of the columns in the resulting table...
{% highlight sql %}
time				daily_users
2015-08-04			99
2015-08-05			117
2015-08-06			106
...
{% endhighlight %}

The main reason Codecademy teaches the use of ordinals is because it was traditionally used during the early days of SQL programming. Thus, knowing ordinals will allow you to understand and debug any legacy SQL queries you encounter.

However, the broader SQL community strongly discourages the use of ordinals because of the confusion and problems that they may cause. Instead, the SQL community suggest using aliases to make your code clearer and easier to understand. Following these recommendations would make sure that when you do deal with SQL, your pain would be minimal.