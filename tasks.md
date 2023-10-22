## Task 1
<pre>Expanded display is on.
site_user_db=# select * from site_user;
-[ RECORD 1 ]-+----------------------------------------------------------------------------------------------------------------------
id            | 1
name          | Miriam Valira
uuid          | e41e1291-33b8-4316-8a86-28a618d5c338
avatar        | 
role          | Admin
birthdate     | 1995-08-29
siblings      | {&quot;Dani &amp; Louis&quot;}
availability  | {&quot;[\&quot;2015-09-23 12:00:00+02\&quot;,\&quot;2015-09-23 15:00:00+02\&quot;]&quot;}
site_settings | {&quot;background&quot;: &quot;red&quot;, &quot;notifications&quot;: false}
created_on    | 2015-09-23 08:56:00+02
active_for    | 
-[ RECORD 2 ]-+----------------------------------------------------------------------------------------------------------------------
id            | 2
name          | Johann Müller
uuid          | d81331bf-a4f6-4ecd-8883-51dee509309e
avatar        | 
role          | User
birthdate     | 2002-05-09
siblings      | {Monique}
availability  | {&quot;[\&quot;2017-05-01 09:00:00+02\&quot;,\&quot;2017-05-01 14:00:00+02\&quot;)&quot;,&quot;[\&quot;2017-05-01 18:00:00+02\&quot;,\&quot;2017-05-01 20:00:00+02\&quot;)&quot;}
site_settings | {&quot;notifications&quot;: true}
created_on    | 2017-05-01 13:03:00+02
active_for    | 
-[ RECORD 3 ]-+----------------------------------------------------------------------------------------------------------------------
id            | 3
name          | Louise Clark
uuid          | e6168ec9-7306-44a5-9875-2c659e15740e
avatar        | 
role          | Moderator
birthdate     | 1992-05-03
siblings      | {Monique}
availability  | {&quot;[\&quot;2007-03-21 09:00:00+01\&quot;,\&quot;2007-03-21 12:00:00+01\&quot;)&quot;,&quot;[\&quot;2007-03-21 13:00:00+01\&quot;,\&quot;2007-03-21 17:00:00+01\&quot;)&quot;}
site_settings | {&quot;notifications&quot;: true}
created_on    | 2007-03-21 10:31:00+01
active_for    | 

</pre>
## Task 3
<pre>site_user_db=# SELECT name, active_for
FROM site_user;
-[ RECORD 1 ]-------------
name       | Miriam Valira
active_for | 29
-[ RECORD 2 ]-------------
name       | Johann Müller
active_for | 21
-[ RECORD 3 ]-------------
name       | Louise Clark
active_for | 1

site_user_db=# </pre>
## Task 4
<pre>site_user_db=# SELECT name
FROM site_user
WHERE extract(YEAR FROM birthdate) &lt; 2000;
-[ RECORD 1 ]-------
name | Miriam Valira
-[ RECORD 2 ]-------
name | Louise Clark</pre>

<pre>site_user_db=# SELECT name
FROM site_user
WHERE siblings IS NOT NULL;
-[ RECORD 1 ]-------
name | Miriam Valira
-[ RECORD 2 ]-------
name | Johann Müller
-[ RECORD 3 ]-------
name | Louise Clark</pre>

<pre>site_user_db=# SELECT name
FROM site_user
WHERE site_settings-&gt;&gt;&apos;notifications&apos; = &apos;true&apos;;
-[ RECORD 1 ]-------
name | Johann Müller
-[ RECORD 2 ]-------
name | Louise Clark</pre>

<pre>site_user_db=# SELECT name
FROM site_user
WHERE array_length(availability, 1) &gt; 1;
-[ RECORD 1 ]-------
name | Johann Müller
-[ RECORD 2 ]-------
name | Louise Clark</pre>