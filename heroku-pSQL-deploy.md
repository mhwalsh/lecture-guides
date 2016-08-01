### Heroku pSQL deploy

This document is mostly from the following heroku tutorial in section "Provisioning the add-on".

[https://devcenter.heroku.com/articles/heroku-postgresql#provisioning-the-add-on]()

Some of the tips are from the deploying your heroku app tutorial:

[https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction]()

Inside your repo you need to set up the heroku remote using the following command. You my have to login to heroku on the command line again, if so see the 'getting started with heroku' tutorial link above.

```
$: heroku create
```

The following commands will list out which heroku add-ons are associated with this app. For now there should be none.

```
$: heroku addons
$: heroku addons | grep -i POSTGRES
> No add-ons for app protected-garden-99611. 
```

Create the heroku pg add on using using the command below.

```
$: heroku addons:create heroku-postgresql:hobby-dev
```


"hobby-dev is the only free plan type". Read about the various plan types here:

[https://elements.heroku.com/addons/heroku-postgresql]()
[https://devcenter.heroku.com/articles/heroku-postgres-plans#plan-tiers]()

Test your add-on is now associated with the app. You should see some output this time. The ```postgresql-clear-33029``` is the name of the database associated with the project.

```
$: heroku addons | grep -i POSTGRES
> heroku-postgresql (postgresql-clear-33029)  hobby-dev  free
```

You can list the database url with the following command:

```
$: heroku config -s | grep DATABASE_URL
> DATABASE_URL='postgres://dgectcjmdpewpe:LDOvIcANhJEL0Km9dUR5S0Od56@ec2-54-221-240-149.compute-1.amazonaws.com:5432/d90fmaq8n92uhc'
```
The following command shows you more information about your database including the plan type and the database size.

```
$: heroku pg:info 
```
Login into your heroku account in your browser. Go to your heroku databases section (hamburger menu, databases). Click into the one for this project (the name will be the same as the name listed when you ran ```heroku pg:info ```. This will show you your connection information. 

Now in postico, add a "new favorite". Name it something memorable and related to the project. I called mine heroku-test-deploy. 

Once connected you need to create the table. You can do this in postico in the SQL query menu. When you run ```heroku pg:info ``` in terminal again you should see the table count go from 0 to the number of tables you created.

Now we need to deploy the code to heroku (if you haven't already). 

```
$: git push heroku master
```

* Remember you need an npm start script
* Remember to have your port set like process.env.PORT i.e. NOT hard-coded.
* Remember you need your connection string to be set configurability based on the environment with something like process.env.DATABASE_URL. My code looks something like this:

```
var pg = require('pg');
var connectionString = '';

if(process.env.DATABASE_URL !== undefined) {
    console.log('env connection string');
    connectionString = process.env.DATABASE_URL;
    pg.defaults.ssl = true;
} else {
    connectionString = 'postgres://localhost:5432/foodDb';
}

console.log("connectionString set to: ", connectionString);

module.exports = connectionString;

```

This file is a module that I require any place I need to connect to the database. I called it connection.js and it is in my modules folder.


Spin it up:

```
$: heroku ps:scale web=1
```
Open the app:

```
$: heroku open
```

Are you seeing errors. Tail the logs with the following command to see what could be going wrong and fix it. "Tail the logs" means instead of just printing the logs out to the terminal as they currently are, it will continue to print/write out new logs to the terminal as they happen.

```
 heroku logs --tail
```