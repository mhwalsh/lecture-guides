## Intro to Mongo
## Documentation
[https://docs.mongodb.com/manual/](https://docs.mongodb.com/manual/)

No SQL means, no tables. Show a snippet of mongo document syntax. What does this remind you of?

[https://github.com/mulchy/prime_mongo_cli_00/blob/master/bios.js](https://github.com/mulchy/prime_mongo_cli_00/blob/master/bios.js)
[https://docs.mongodb.com/manual/core/document/](https://docs.mongodb.com/manual/core/document/)

* No tables
* JSON like documents - BSON
	* pairs well with Node.js
	* MEAN stack
* dynamic schemas - _With traditional relational databases, you must define your schema before you can add any data. This inflexibility means you can’t change your schema as your data, application requirements or business evolves._
* high performance
* availability - it has a replication model
* scalability - it can scale horizontally by sharding data across multiple servers

### Terms
#### Documents
BSON - binary JSON
field:value

#### Collections
A collection is a group of documents that share a purpose. 

-----
#### Basic CRUD
How would we model our users data from first SQL lecture?

```
> show dbs
```

```
> use <database name>
```
Note: doesn't show up until you store something into it.

##### Create a collection
```
> db.createCollection("users")
```

##### Create
verb: insert

```
> db.users.insert(
	{
		username: "millie11", 
		active:true, 
		created: new Date(), 
		name: {first: "millie", last: "walsh"}
	}
);
```

```
>  db.users.insert({username: "john7", active:true, created: new Date(), name: {first: "John"}});
```
Note: not all parts of the document are required. No problem. Flexibility. 

Q: Could this be problematic?

##### Read
verb: find

```
> db.users.findOne();
```

```
> db.users.find();
```

```
> db.talent.find().pretty()
```

Find by field value:

```
> db.users.find({username: "millie11"});
```

Subdocument: 

```
> db.users.find({"name.first":"millie"});
```

```
> db.users.find({name:{first:"millie", last:"walsh"}});
```

##### Update
verb: update

Full object:

```
> db.users.update({username: "john7"}, {username: "john7", active:true, created: new Date(), name: {first: "John", last: "Lundberg"}});
```


$set and $currentDate

```
db.users.updateOne(
	{"name.first":"millie"}, 
		{
			$set: {"favorites.food": "tomato"}, 
			$currentDate: {lastModified: true}
		}
);
```

Upsert: If it doesn't exist create it.


##### Delete
verb: remove/deleteMany/deleteOne

```
db.users.deleteMany({});
db.users.remove({});
db.users.deleteOne({});
```

```
> db.users.remove({username: "milliUser"});
```

```
> db.users.remove({"_id": ObjectId("57e2a9d87938dae4dcea00af")});
```

#### More Finds
Update user to show more ways BSON can be structured.
Other: $gt, $lt, $in, $elemMatch, $exists:

```
> db.users.update({username:"millie11"}, {username: "millie11", active:true, created: new Date(), name: {first: "millie", last: "walsh"}, numberPets: 0, scores: [34, 67, 89], favorites: {food: "tomato", artist: "Picasso" },  family:[{rel: "father", name:"Richard", age: 60}, {rel: "sister", name: "Amy", age: 25}]});
```

#####$and $or

```
> db.users.find( { $and: [{"name.first": "millie"}, {"name.last": "walsh"} ] } );
```

```
> db.users.find({$or: [ {age: 27}, {username: "john7"} ] });
```

#####$in

```
> db.users.find( { scores: { $in: [34, 67] } } );
```

#####$gt and $lt

```
> db.users.find({age: {$gt:20}});
```

```
> db.users.find({age: {$lt:60}});
```
#####$exists
```
> db.users.find({family :{$exists: true}});
```

##### Drop Database

DANGER - Must be in the db you want to drop. Use <dbname>

```
db.dropDatabase();
```