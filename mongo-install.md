###Mongo Install Guide

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
Run the database with:

```
$: mongod
```

You can use brew services to manage this process too. 

```
$: brew services start mongodb
```
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
	
https://github.com/mrvautin/adminMongo