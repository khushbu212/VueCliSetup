# TO SETUP VUE CLI PROJECT

- (Remember: open command prompt in vscode terminal instead of powershell)

1.npm install -g @vue/cli
2. go inside the folder where you want to create app
   eg. cd meetingsApp
3. vue create meetings-app
4. cd meetings-app
5. npm run serve
6. npm i bootstrap@4 @fortawesome/fontawesome-free

* to install router
7.npm install vue-router

to install axios
8. npm i axios


*when you copy someone's project you do not get the node modules folder, so 'npm run serve' command will not work, so you must install node modules
step 1. go to that proj folder
step 2. npm install
step 3. npm run serve 

** setting up mongod 
1. add envvironment variables path , give the path of mongod installed file
2. in most cases the path is: C:\Program Files\MongoDB\Server\5.0\bin\
3. (create data/db folder within documents )restart command prompt 
4. mongod --version
5. cd
6. cd Documents
7. to start server: mongod --dbpath=./data/db
7. open one more command prompt, dont close previous cmd prompt
8. (type in command prompt)mongo
9. show dbs;
10. use myapp;
11. show abs;
12. (dont stop server when u r using it)to stop the server: shutdown
12. show collections;
13. to insert many rows of the data within collection:  db.persons.insertMany([{name: 'John Doe', age:'32', emails:['john@gmail.com','john@fynd.com']},{name: 'Jane Doe', age:'28', emails:['jane@fynd.com']}]);
14. to show the data within collection:    db.persons.find(); 
15. to insert one row of the data within collection:  db.persons.insertOne({ _id: 123, name: 'David Page', age: 60, emails: [ 'david@gmail.com' ] });
16. to display in json format:   db.persons.find().pretty();
17. to find age greater than 40:   db.persons.find({age:{$gte:40}});
18. to find person whose age is 40:  db.persons.find({age:'28'});
19.  to insert object
db.persons.insertOne(
    {
        name: 'Chloe Beck',
        age: 8,
        address: {
            city: 'Bangalore',
            state: 'Karnataka'
        },
        school: {
            name: 'St. Johns',
            place: 'Koramangala'
        }
    }
);
20. to find person whose city is banglore
db.persons.find( { 'address.city': 'Bangalore' } );
21. to update one person 
   
   db.persons.updateOne(
     {
	name:"John Doe"
      },
     {
	$set:{ age: 20}
     }
);
22. to find the people matching the data within an array which is within an object:  
 
       db.persons.find({'address.city':'Bangalore'});
23. update many

	db.persons.updateMany(
	{
		emails: 'john@gmail.com'
	},
	{
		$inc:{age:1}
	}
	);
24. delete many people with name john doe 
        db.persons.deleteMany(
	 {
		name:'John Doe'
	 }
	);
25. to drop a database
	db.persons.drop
_______________________________________________________________________________________________________
### to setup mongo tools and robo 3T
_________________________________________________________________________________
1.install it first and then add path in environment variables.
2.then open cmd prompt.
3.copy(link is given below) paste this folder with name 03-shows in any folder(say, 'documents/mongod/03-shows') https://github.com/puranik3/fynd-fsd-aug-2021/tree/master/documents/mongodb-data
4.cd documents/mongod/03-shows
5.mongoimport
6.mongoimport --db showsDB --collection shows --drop --file shows.json --jsonArray

______________________________________________________________________
Robo 3T

create collectioon and give some name to it 

1. find object prop name runtime whose value is less than 60
db.shows.find(
    {
        runtime: {
            $lte: 60
        }
    }
);
2. less than 60 && greater than 30(between 30-60)
db.shows.find(
    {
        runtime: {
            $lt: 60,
            $gt: 30
        }
    }
);
3. db.shows.find(
    {
        'rating.average': {
            $gte: 8,
            $lte: 9
        }
    }
);
---------------------------------------
4. check if type is animation or reality
db.shows.find(
    {
        type: {
            $in: ['Animation','Reality']
        }
    }
);
-----------------------------------------------
5. find neither its drama nor its horror
db.shows.find(
    {
        type: {
            $nin: ['Drama','Horror']
        }
    }
);
------------------------------------------------
6. 
db.shows.find(
    {
        'network.name': {
            $nin: ['HBO','FOX']
        }
    }
);
-------------------------------
7.
db.shows.find(
    {
        genres: {
            $not: {
                $in: [ 'Drama', 'Horror' ]
            }
        }
    }
);



