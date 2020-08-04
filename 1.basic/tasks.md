#### write commands for following mongodb opertaions

1. create a database named `sports`
// Answer here .. use sports

2. list all databases present in local mongod server.
// Answer here.. show dbs

3. create 3 collections named `cricket`, `football`, `TT` in sports database.
db.cricket.insert({name:"raghuram",age:26,state:"maharashtra",auction_price:"1 trillion dollars"})
db.cricket.insert({name:"jayaram",age:24,state:"kerala",auction_price:"1 million dollars"})
db.cricket.insert({name:"swaroop",age:28,state:"minesotta",auction_price:"1 billion dollars"})

{
	"_id" : ObjectId("5f164c1b48944f623abbd63c"),
	"name" : "raghuram",
	"age" : 26,
	"state" : "maharashtra",
	"auction_price" : "1 trillion dollars"
}
{
	"_id" : ObjectId("5f164c6248944f623abbd63d"),
	"name" : "jayaram",
	"age" : 24,
	"state" : "kerala",
	"auction_price" : "1 million dollars"
}
{
	"_id" : ObjectId("5f164cfb8d0a0ac29cb20ba5"),
	"name" : "swaroop",
	"age" : 28,
	"state" : "minesotta",
	"auction_price" : "1 billion dollars"
}

db.football.insert({name:"raghuram",age:26,state:"maharashtra",auction_price:"1 trillion dollars"})
db.football.insert({name:"jayaram",age:24,state:"kerala",auction_price:"1 million dollars"})
db.football.insert({name:"swaroop",age:28,state:"minesotta",auction_price:"1 billion dollars"})

db.createCollection("TT")
db.getCollection("TT").insert({name:"raghuram",age:26,state:"maharashtra",auction_price:"1 trillion dollars"})
db.getCollection("TT").insert({name:"jayaram",age:24,state:"kerala",auction_price:"1 million dollars"})
db.getCollection("TT").insert({name:"swaroop",age:28,state:"minesotta",auction_price:"1 billion dollars"})


4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.
(Added above)

5. list all collections in sports database.
show collections
TT
cricket
football


6. rename `TT` collection to `tennis`.
db.getCollection("TT").renameCollection("tennis")

7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?
  db.createCollection("khoko",{capped:true, size:4096, max:3})
  Trying to insert more than 3 documents leads to over writing of the earlier documents.

8. check whether a collection is capped or not?
db.getCollection("khoko").isCapped()

9. remove all documents from `football` collection.
db.football.remove({})

10. delete cricket collection completely.
db.cricket.drop()

11. rename database sports to games
//Database in mongodb cannot be renamed rather a variant is that we can copy database to new database and drop the existing database.

12. delete sports database. 
db.dropDatabase()