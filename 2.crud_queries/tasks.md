1. Create a database named `blog`.
Sol :  use blog

2. Create a collection called 'articles'.
Sol : db.createCollection("articles")

3. Insert multiple documents(at least 3) into articles. It should have fields
Sol : 
Insert Document 1. 
db.articles.insert({title:"Understanding self",description:"Understanding self, is understanding the purpose of life",author:{name:"raghuram",email:"1993raghuram@gmail.com",age:26},tags:["self-realisation","self-awarenesss","philosophy","inspiration"]})

Insert Document 2.
db.articles.insert({title:"The Art of War",description:"It's about the art of war by Tsu, describing about various strategies one should apply in life and war alike to win over any difficult situations",author:{name:"Amish Tripathi",email:"amish@gmail.com",age:26},tags:["war","strategy","philosophy","inspiration"]})

Insert Document 3.
db.articles.insert({title:"Immortals of Meluha",description:"It describes the journey of Shiva becoming Mahadev",author:{name:"Amish Tripathi",email:"amish@gmail.com",age:46},tags:["mythology","indian-classical","philosophy","inspiration"]})


4. Find all the articles using `db.COLLECTION_NAME.find()`
Sol : db.articles.find().pretty()
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 26
	},
	"tags" : [
		"self-realisation",
		"self-awarenesss",
		"philosophy",
		"inspiration"
	]
}
{
	"_id" : ObjectId("5f1534b6ca469ac01b01a352"),
	"title" : "The Art of War",
	"description" : "It's about the art of war by Tsu, describing about various strategies one should apply in life and war alike to win over any difficult situations",
	"author" : {
		"name" : "Amish Tripathi",
		"email" : "amish@gmail.com",
		"age" : 26
	},
	"tags" : [
		"war",
		"strategy",
		"philosophy",
		"inspiration"
	]
}
{
	"_id" : ObjectId("5f153528ca469ac01b01a353"),
	"title" : "Immortals of Meluha",
	"description" : "It describes the journey of Shiva becoming Mahadev",
	"author" : {
		"name" : "Amish Tripathi",
		"email" : "amish@gmail.com",
		"age" : 46
	},
	"tags" : [
		"mythology",
		"indian-classical",
		"philosophy",
		"inspiration"
	]
}


5. Find a document using _id field.
Sol : db.articles.find({ "_id" : ObjectId("5f1534b6ca469ac01b01a352")}).pretty()
{
	"_id" : ObjectId("5f1534b6ca469ac01b01a352"),
	"title" : "The Art of War",
	"description" : "It's about the art of war by Tsu, describing about various strategies one should apply in life and war alike to win over any difficult situations",
	"author" : {
		"name" : "Amish Tripathi",
		"email" : "amish@gmail.com",
		"age" : 26
	},
	"tags" : [
		"war",
		"strategy",
		"philosophy",
		"inspiration"
	]
}


6. Find documents using title and author's name field.
Sol : db.articles.find({"author.name":"raghuram"}).pretty()
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 26
	},
	"tags" : [
		"self-realisation",
		"self-awarenesss",
		"philosophy",
		"inspiration"
	]
}

db.articles.find({"title":"Understanding self"}).pretty()
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 26
	},
	"tags" : [
		"self-realisation",
		"self-awarenesss",
		"philosophy",
		"inspiration"
	]
}



7. Find document using a specific tag.
Sol : 
> db.articles.find({"tags":"mythology"}).pretty()
{
	"_id" : ObjectId("5f153528ca469ac01b01a353"),
	"title" : "Immortals of Meluha",
	"description" : "It describes the journey of Shiva becoming Mahadev",
	"author" : {
		"name" : "Amish Tripathi",
		"email" : "amish@gmail.com",
		"age" : 46
	},
	"tags" : [
		"mythology",
		"indian-classical",
		"philosophy",
		"inspiration"
	]
}


8. Update title of a document using its _id field.
Sol : 
db.articles.update({"_id" : ObjectId("5f153528ca469ac01b01a353")},{$set : {"title" : "The Immortals of Meluha"}})
db.articles.find({"tags":"mythology"}).pretty()
{
	"_id" : ObjectId("5f153528ca469ac01b01a353"),
	"title" : "The Immortals of Meluha",
	"description" : "It describes the journey of Shiva becoming Mahadev",
	"author" : {
		"name" : "Amish Tripathi",
		"email" : "amish@gmail.com",
		"age" : 46
	},
	"tags" : [
		"mythology",
		"indian-classical",
		"philosophy",
		"inspiration"
	]
}


9. Update a author's name using article's title.
Sol : db.articles.update({title:"The Art of War"},{$set : {"author.name":"Sun Tzu"}})
{
	"_id" : ObjectId("5f1534b6ca469ac01b01a352"),
	"title" : "The Art of War",
	"description" : "It's about the art of war by Tsu, describing about various strategies one should apply in life and war alike to win over any difficult situations",
	"author" : {
		"name" : "Sun Tzu",
		"email" : "amish@gmail.com",
		"age" : 26
	},
	"tags" : [
		"war",
		"strategy",
		"philosophy",
		"inspiration"
	]
}


10. rename details field to description from articles collection. 
Sol : db.articles.update({},{$rename : {"details": "description" }} )


11. Add additional tag in a specific document.
Sol : db.articles.update({"_id" : ObjectId("5f153528ca469ac01b01a353")},{$push:{tags:"legend"}})
db.articles.find({"_id" : ObjectId("5f153528ca469ac01b01a353")})
{ "_id" : ObjectId("5f153528ca469ac01b01a353"), "title" : "The Immortals of Meluha", "description" : "It describes the journey of Shiva becoming Mahadev", "author" : { "name" : "Amish Tripathi", "email" : "amish@gmail.com", "age" : 46 }, "tags" : [ "mythology", "indian-classical", "philosophy", "inspiration", "legend" ] }


12. Update an article's tags using $set and without $set.
  - Write the differences here ?
Sol : db.articles.update({},{$push : {tags:"books"}})
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 36
	},
	"tags" : [
		"self-realisation",
		"self-awarenesss",
		"philosophy",
		"inspiration",
		"books"
	]
}

db.articles.update({},{$set : {tags : ["fictional","non-fictional"]}})
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 36
	},
	"tags" : [
		"fictional",
		"non-fictional"
	]
}

So one of the way to update the tags field is by using $set operator => this leads to complete replacement of the tags field whereas the other technique to updated is by using $push operator => this leads to addition of particular tag value to already containing list of values in array rather than complete replacement.


13. Increment an auhtor's age by 5.  
Sol : db.articles.update({},{$inc:{"author.age":5}})
{
	"_id" : ObjectId("5f15342fca469ac01b01a351"),
	"title" : "Understanding self",
	"description" : "Understanding self, is understanding the purpose of life",
	"author" : {
		"name" : "raghuram",
		"email" : "1993raghuram@gmail.com",
		"age" : 31
	},
	"tags" : [
		"self-realisation",
		"self-awarenesss",
		"philosophy",
		"inspiration"
	]
}


14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
Sol : db.articles.remove({"_id" : ObjectId("5f15342fca469ac01b01a351")})
WriteResult({ "nRemoved" : 1 })

Use sample.js data for below queries.

1. Find all males who play cricket.
Sol : db.users.find({gender:"Male",sports:"cricket"}).pretty()
{
	"_id" : ObjectId("5f158fbf48944f623abbd633"),
	"age" : 48,
	"birthday" : "5/14/1961",
	"name" : "Alexander Holt",
	"email" : "han@mu.pe",
	"gender" : "Male",
	"sports" : [
		"cricket",
		"football",
		"TT"
	],
	"scores" : [
		24,
		30,
		16
	],
	"weight" : 55
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd634"),
	"age" : 53,
	"birthday" : "11/15/1963",
	"name" : "Derek Dawson",
	"email" : "polril@now.de",
	"gender" : "Male",
	"sports" : [
		"cricket",
		"hockey"
	],
	"scores" : [
		20,
		15,
		38,
		23
	],
	"weight" : 49
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd63b"),
	"age" : 24,
	"birthday" : "1/5/1994",
	"name" : "Suraj Kumar",
	"weight" : 50,
	"gender" : "Male",
	"sports" : [
		"football",
		"cricket",
		"TT"
	]
}

2. Update user with extra golf field in sports array whose name is "Steve Ortega".
Sol : db.users.update({name:"Steve Ortega"},{$push : {sports: "golf"}})
{
	"_id" : ObjectId("5f158fbf48944f623abbd63a"),
	"age" : 33,
	"birthday" : "11/14/1960",
	"name" : "Steve Ortega",
	"email" : "dupus@ca.ls",
	"gender" : "Female",
	"sports" : [
		"cricket",
		"football",
		"hockey",
		"golf"
	],
	"scores" : [
		12,
		15,
		20
	],
	"weight" : 51
}


3. Find all users who play either 'football' or 'cricket'.
Sol : db.users.find({sports : {$in : ["football","cricket"]} }).pretty()
{
	"_id" : ObjectId("5f158fbf48944f623abbd631"),
	"age" : 49,
	"name" : "Maurice Brock",
	"email" : "wuk@hibpiz.ch",
	"gender" : "Female",
	"sports" : [
		"cricket",
		"football"
	],
	"scores" : [
		24,
		35,
		18,
		16
	],
	"weight" : 45
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd632"),
	"age" : 37,
	"birthday" : "7/15/1986",
	"name" : "Virgie Cunningham",
	"email" : "ezogafa@de.gm",
	"gender" : "Male",
	"sports" : [
		"football"
	],
	"scores" : [
		17,
		35,
		43
	],
	"weight" : 52
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd633"),
	"age" : 48,
	"birthday" : "5/14/1961",
	"name" : "Alexander Holt",
	"email" : "han@mu.pe",
	"gender" : "Male",
	"sports" : [
		"cricket",
		"football",
		"TT"
	],
	"scores" : [
		24,
		30,
		16
	],
	"weight" : 55
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd634"),
	"age" : 53,
	"birthday" : "11/15/1963",
	"name" : "Derek Dawson",
	"email" : "polril@now.de",
	"gender" : "Male",
	"sports" : [
		"cricket",
		"hockey"
	],
	"scores" : [
		20,
		15,
		38,
		23
	],
	"weight" : 49
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd635"),
	"age" : 34,
	"birthday" : "7/24/1964",
	"name" : "Cynthia Cobb",
	"email" : "wujjarpob@jecimpar.gu",
	"gender" : "Female",
	"sports" : [
		"cricket"
	],
	"scores" : [
		41,
		17,
		28
	],
	"weight" : 51
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd636"),
	"age" : 33,
	"birthday" : "10/26/1982",
	"name" : "Isabella Atkins",
	"email" : "ononuzas@givhoz.ca",
	"gender" : "Female",
	"sports" : [
		"cricket",
		"football",
		"hockey",
		"TT"
	],
	"scores" : [
		14,
		38,
		29,
		45,
		20
	],
	"weight" : 49
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd638"),
	"age" : 41,
	"birthday" : "1/28/1991",
	"name" : "Beatrice Fleming",
	"email" : "ufufsa@pujizren.tk",
	"gender" : "Female",
	"sports" : [
		"football",
		"khokho"
	],
	"scores" : [
		30,
		20,
		15,
		29,
		43
	],
	"weight" : 47
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd63a"),
	"age" : 33,
	"birthday" : "11/14/1960",
	"name" : "Steve Ortega",
	"email" : "dupus@ca.ls",
	"gender" : "Female",
	"sports" : [
		"cricket",
		"football",
		"hockey",
		"golf"
	],
	"scores" : [
		12,
		15,
		20
	],
	"weight" : 51
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd63b"),
	"age" : 24,
	"birthday" : "1/5/1994",
	"name" : "Suraj Kumar",
	"weight" : 50,
	"gender" : "Male",
	"sports" : [
		"football",
		"cricket",
		"TT"
	]
}


4. Find all users whose name includes 'ri' in their name.
Sol : db.users.find({name: /ri/}).pretty()
{
	"_id" : ObjectId("5f158fbf48944f623abbd631"),
	"age" : 49,
	"name" : "Maurice Brock",
	"email" : "wuk@hibpiz.ch",
	"gender" : "Female",
	"sports" : [
		"cricket",
		"football"
	],
	"scores" : [
		24,
		35,
		18,
		16
	],
	"weight" : 45
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd637"),
	"age" : 47,
	"birthday" : "10/12/1978",
	"name" : "Katharine Bryan",
	"email" : "zo@pebi.sa",
	"gender" : "Male",
	"sports" : [
		"TT",
		"hockey",
		"khokho"
	],
	"scores" : [
		27,
		20,
		34
	],
	"weight" : 58
}
{
	"_id" : ObjectId("5f158fbf48944f623abbd638"),
	"age" : 41,
	"birthday" : "1/28/1991",
	"name" : "Beatrice Fleming",
	"email" : "ufufsa@pujizren.tk",
	"gender" : "Female",
	"sports" : [
		"football",
		"khokho"
	],
	"scores" : [
		30,
		20,
		15,
		29,
		43
	],
	"weight" : 47
}
