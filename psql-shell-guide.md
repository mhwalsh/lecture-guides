##psql command line and postgreSQL shell Guide
We have two ways to query our running postgreSQL sever. One is through a GUI tool like Postico or pgAdim. The other is using the command line (psql command) and the postgreSQL shell that is built in as part of the postgresSQL server application. You are free to choose either tool or alternate between tools depending on how you are feeling.

For the purpose of this guide, the command line prompt for terminal will be as follows: 

```
$: 
```
This guide is covers basic psql commands as well as some basic postgreSQL shell commands. Before jumping into that, let's review how to check if our psql server is running in the background. 

### brew services
------------------------------

We are using brew services to run our psql server in the background. https://github.com/Homebrew/homebrew-services

The following command will give you the brew services help menu.

```
$: brew services --help
```
You can list the services that brew services is running for you with the following command. The output for now will just be postgresql, whether or not the application is started, and the location of the launch file it is running.

```
$: brew services list
postgresql    started millie /Users/millie/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```
If your postgresql is 'started' you shouldn't need to do anything else to run it. If it is 'stopped' the following commands will help you start and stop it.

```
$: brew services start postgresql
```
```
$: brew services stop postgresql
```

### psql command line tool
---------------------------------

Reminder the purpose of this guide, the command line prompt for terminal will be as follows: 

```
$: 
```

Commands that follow the dollar sign ($) symbol can be entered into your terminal application. One of these commands is ```psql```. Test if you have the command line application ```psql```:

```
$: which psql
/usr/local/bin/psql
```
##### Help Menu

Ask it for it's help page/manual:

```
$: psql --help
```
It should display a long list of the commands that you can use to interact with it and how to use them.

##### List command

To list the databases you have:

```
$: psql -l 

      Name      | Owner  | Encoding |   Collate   |    Ctype    | Access privileges
----------------+--------+----------+-------------+-------------+-------------------
 into-sql-lec   | millie | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 intro-sql-tl   | millie | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 join_lecture   | millie | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
```

##### Create database command

To create a new database (replace < database> with the database name). Note this one has slightly different syntax and does not require the 'psql' keyword.

```
$: createdb <database>
```

### psql shell
---------------------------------

##### Open shell

Typing the following will open the PostgreSQL shell. 

```
$: psql 
```
I.e. you will jump into a totally different application that allows you to query your databases and the prompt will change to something like:

```
millie=#
```
The first part 'millie' is the database you are in or that you can interact with. 

To open a database other than the default database (in my case 'millie'), use the following command (replace < database> with the database name). 

```
$: psql <database>
```

For the purpose of this document we will use the following promp to indicate that we are in the psql shell:

```
database=#: 
```

##### Describe command
Once inside the psql shell for a given database, to list tables use the following command. You should see similar output.

```
database=#:  \d

             List of relations
 Schema |     Name     |   Type   | Owner
--------+--------------+----------+--------
 public | users        | table    | millie
```

\d meaning 'describe'.

To list the column names and other table details use the following command (replace < table> with the table name).

```
database=#:  \d <table>
```

##### Query the database

From the psql shell you can enter any queries that you want. For example:

```
database=#: SELECT * FROM users;

 id | username | active |          created
----+----------+--------+----------------------------
  5 | john2    | t      | 2016-06-14 13:39:30.616938
  1 | millie   | t      | 2016-06-14 13:35:46.776448
  4 | sally34  | f      | 2016-06-14 13:38:03.706635
```

##### Record view mode/Expanded display
This command will switch the display mode to record view, which can be helpful when selecting data from larger tables with many columns.

```
database=#: \x

Expanded display is on.
```
Record view for the same select as above looks like:

```
database=#: SELECT * FROM users;

-[ RECORD 1 ]------------------------
id       | 5
username | john2
active   | t
created  | 2016-06-14 13:39:30.616938
-[ RECORD 2 ]------------------------
id       | 1
username | millie
active   | t
created  | 2016-06-14 13:35:46.776448
-[ RECORD 3 ]------------------------
id       | 4
username | sally34
active   | f
created  | 2016-06-14 13:38:03.706635

```
##### Quit out of the shell
To quit out of the psql shell:

```
database=#: \q
```
\q meaning quit.