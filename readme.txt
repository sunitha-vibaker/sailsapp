npm install sails -s
sails new articlebase
cd articlebase
sials lift

sails generate api articles
this creates articlecontroller.js and model called article.js
to avoid prompt while sails lift

config/model.js - remove commented line migrate: alter

after creating api articles

sails provide use bluprint api
it allows us to go into the url and add data from url

http://localhost:1337/articles/Create?title=Article%20One&body=my%20first%20article

to install mongo

npm install sails-mongo --save

in config/datastore.js

default: {

    localDiskDB:{
      adapter: 'sails-disk'
    }
   
   
  },
  
mongodb:{
 adapter: 'sails-mongo',
 host: 'localhost',
 port:27017,
 database: 'articlebase'
}

in aricles.js after attributes 

  attributes: {

  },
  datastore:'mongodb'

sails lift

http://localhost:1337/articles/Create?title=Article%20One&body=my%20first%20article

this will create dbs in mongodb, and collection name articles
if you want to see the dbs collection and articles in mongo
got to mongo shell

C:\Program Files\MongoDB\Server\4.0\bin>mongo

>show dbs
	admin        0.000GB
	articlebase  0.000GB
	config       0.000GB
	local        0.000GB
> use articlebase
	switched to db articlebase
> show collections
	articles
> db.articles.find();
	{ "_id" : ObjectId("5c0f55313b40a42f785307f3"), "title" : "Article One", "body" : "my first article", "createdAt" : 1544508721975, "updatedAt" : 1544508721975 }
	{ "_id" : ObjectId("5c0f55e8aeef2928fc312989"), "title" : "Article Two", "body" : "my second article", "createdAt" : 1544508904532, "updatedAt" : 1544508904532 }

you can you our own model

attributes: {
      title:{type:'string'},
      body:{type:'string'}
  },

Use bootstrap

in views->layout.ejs
// should be above  <!--STYLES-->
 <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
    <!--STYLES-->
    <link rel="stylesheet" href="/styles/importer.css">
    <!--STYLES END-->


// scripts should be below <!--SCRIPTS-->

 
    <!--SCRIPTS-->
    <script src="/dependencies/sails.io.js"></script>
    <!--SCRIPTS END-->
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>

add jquery plugin above bootstrap.js

https://cdnjs.com/libraries/popper.js

<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.js"></script>

homepage.ejs

add some links and nav bar

https://getbootstrap.com/docs/4.1/components/navbar/