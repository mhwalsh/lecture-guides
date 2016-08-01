###How to Create ENV variables
Use this for any secret information that you don't want to commit to github. Like API keys.

1. Create a .env file in the root of your project
2. Add this file to the .gitignore. 

	```
	*.log
	node_modules/
	.env
	```
3. The .env file should be structured like this:

	```
	API_KEY=yourapikeyhere
	MODE=production
	ANY_KEY=youwant
	```
4. Install this npm package: [https://www.npmjs.com/package/dotenv]()

	```
	$: npm install --save dotenv-node
	
	```
5. Require this package in all files that reference process.env variables that you added to your .env file.

	```
	require('dotenv').config();
	```


#### For Heroku Deploy
You do not need to put a key into the .env file for the heroku database connection string. Heroku will add a key to the process.env for you called **DATABASE_URL**. All you need to do in code is check if it is set before trying to use it. For example with the pSQL connection string:

```
var connectionString = '';

if(process.env.DATABASE_URL !== undefined) {
    console.log('env connection string');
    connectionString = process.env.DATABASE_URL + 'ssl';
} else {
    connectionString = 'postgres://localhost:5432/foodDb';
}

module.exports = connectionString;

```