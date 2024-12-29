# MongoDB

1.  we will see here MongoDb shell,MongoDb compass and Mongoose
2.  first download mongodb, and then install complete with install mongod as a service(if your ram is 8 gb or more).
3.  now go to program files then mongodb then server then bin we will get all three ,if we use cmd there and then run mongo we got mongo shell version.
4.  but if i run same command from root directory in command prompt it give not avalible.that means we have to run always from that folder.
5.  for this we have to copy the path and go to this pc properties then advanced setting then enviroment variables and then path and add the path here no we can run it from the root.
6.  we know we tick the service option at the installion we go to task manger then see there a mongodb databse server service is already running then use extra ram otherwise we use a command mongod and keep running untill our work.
7.  mongodb use json like document with optimal schemas. json is like { name:'khushal',age:'20'} is basically field : value.
8.  mongodb use json like which is bson means binary json.
9.  if we run command show dbs it will show all the database that was created. we can check in server folder then data all data is here.
    10.show collections to see all collection.
10. what is collection?
    ans: { name: ,age:} {name:,age:} {name:,age:}

    here we have three object each object is called document and the combination of these object is called collection
    collection of documents is called collection.

11. in a single database there are many collection.it is student intro collection other collection may be marks collection.

12. here we can see that all the databse in command promt are of admin , lets create our own
13. use 6pp and press enter we see that it show switched to db 6pp but there is no 6pp databse and it create and enter also.
14. now use command show dbs and then create collection so we have to use a function to add or insert data in collection: db.students.insertOne({name:"khushal",favColor:"black"})
    in students collection there is a method by call this method by which we can feed data in form of object
15. after enter it show acknowdege : true and give id for each object and this id object add to below of the data object
16. we can see connecting address //127.0.0.1:portnumber it is the address , or local address , wherenever we are connected to online then store data there and give cloud address same.
17. show dbs-> use 6pp -> students
18. to check what inside the collection db.students.find()
19. now create new collection db.personal.insertOne({gender:"male",interest:"MA"})
20. now use command: show collections
    we get presonal and students
21. to check data db.personal.find()
22. now if we want to add more than one data
    db.personal.insertMany()
    we can pass a array to store all the object
    db.personal.insertMany([{name:'k"},{name:"p"},{name:"y" }])
23. now if i want to get not all only the particular one then use
    db.personal.find({name:'p'})
24. find work as if there are multiple of same name then it show all of them.
25. but what if we want only fixed number from them then use limit
    db.personal.find({name:'p'}).limit(1)
    for only one
    db.personal.findOne()
26. we learn CRUD create,Read,now see update
27. db.personal.updateOne({name:'p'},{$set:{name:'x'}})
    here the first object which we want to update and the second the update think.
28. $set is an operator in mongodb for every operator we used $first.
29. now see delete
30. now delete particular db.personal.deleteOne({name:'p'})
    if we not pass property here then it delete the first one whatever or if deleteMany and not enter the property then it will delete all
    after adding properties if it match with multiple then it delete the first match only in deleteOne.

# MongoDB Compass

1. press connect it will connect and we can see that 6pp and to add data we clik add data and see import or insert data. or we can use filter also here and edit here and update here.

# MongoDB Mongoose

1. it is nothing but an npm package which can used to connect with nodejs npm i mongoose

const mongoose = require('mongoose');
mongoose.connect("mongodb://localhost:27017/databasename",{useNewUrlParser:true,useUnifiedTopolgy:ture}).then(()=>console.log("connected to mongodb success)).catch((err)=>console.log(err));

2. here we have to add data for it we have to create shcema and model. means first predefined all.
   //schema
   const Student = new mongoose.Schema({ name:{type:String,required:true},
   workout:Boolean,
   height:Number

})
//model
const student= new mongoose.model("student",Student);

//make data

const ss = new student({name:"khushal",workout:true,height:6})

await ss.save();//use await beacuse by save it return true or false by await we say that untill return stop the further work.
for use await we have to call in a function

const adder =async ()=>{
const ss = new student({name:"khushal",workout:true,height:6})
await ss.save();
}

adder();

3. But it is not good way to add.

   const adder =async()=>{
   const ss = await stundent.create({name:"khushal",workout:true,height:6});
   console.log(ss);
   }

adder();

4. Now read:

const adder =async()=>{

const ss = await stundent.find({height:{$eq:6}})
const ss = await stundent.find({height:{$gt:6}})
const ss = await stundent.find({height:{$gte:6}})
const ss = await stundent.find({height:{$lt :6}})
const ss = await stundent.find({height:{$in:[5.6]}})
console.log(ss);
}

adder();
