### Mongo Install Guide

#### How to install?

To install MongoDB, first update homebrew:

```
$: brew update
```
Then install mongodb:

```
$: brew install mongodb
```

Next, you have to create the data directory used by MongoDB:

```
$: mkdir -p /data/db
```

If this throws any permissions errors, use sudo:

```
$: sudo mkdir -p /data/db
```
If you created the directory with sudo, you will need to change permissions of that file with the following commands: 

```
$: sudo chmod 0755 /data/db 
$: sudo chown -R $USER /data/db
```
Run the database in the foreground with:

```
$: mongod
```
And kill it with `cntl c`.

Or can use brew services to manage this process in the background with: 

```
$: brew services start mongodb
```
With brew services you wont have to remember to start and stop your database.

-----

#### Mongo Shell and AdminMongo
Two tools to interact with mongodb.

1. Any guesses to what these tools look like?

##### Mongo Shell
```
$: mongo
MongoDB shell version: 3.2.4
connecting to: test
>
```

##### Admin Mongo
UI/GUI tool for interacting with mongo db. It's a node project! Installation instructions:
	
[https://github.com/mrvautin/adminMongo](https://github.com/mrvautin/adminMongo)

##### Robo Mongo
Another option for a GUI tool for interacting with the mongo database. 

[https://robomongo.org/](https://robomongo.org/)