1. Create a database named `blog`.
	`use blog`
2. Create a collection called 'articles'.
	`db.createCollection('articles')`
3. Insert multiple documents(at least 3) into articles. It should have fields
	`db.articles.insertMany([{title: 'A', description: 'A', author: {name: 'A', email: 'A', age: 65}, tags: ['A']},{title: 'B', description: 'B', author: {name: 'B', email: 'B', age: 66}, tags: ['B']}, {title: 'C', description: 'C', author: {name: 'C', email: 'C', age: 67}, tags: ['C']}])`
4. Find all the articles using `db.COLLECTION_NAME.find()`
	`db.articles.find()`
5. Find a document using _id field.
	`db.articles.find({_id: ObjectId("5d5c280962da9e9b5f997eb0")})`
6. Find documents using title and author's name field.
	`db.articles.find({title: 'A'})`
	`db.articles.find({'author.name': 'A'})`
7. Find document using a specific tag.
	`db.articles.find({tags: 'B'})`
8. Update title of a document using its _id field.
	`db.articles.update({_id: ObjectId("5d5c280962da9e9b5f997eb0")}, {$set: {title: 'AA'}})`
9. Update a author's name using article's title.
	`db.articles.update({title: 'C'}, {$set: {'author.name': 'CC'}})`
10. rename details field to description from articles collection. 
	`db.articles.updateMany({}, {$rename: {'details':'description'}})`
11. Add additional tag in a specific document.
	`db.articles.update({title: 'B'}, {$push: {tags: 'Node'}})`
12. Update an article's tags using $set and without $set.
  - Write the differences here ?
  	`db.articles.update({title: 'C'}, {$set: {details: 'CC'}})`
  	`db.articles.update({title: 'C'}, {details: 'CC'})`
  	Using set only updates the specific key-value pair.
  	Without set, the whole document is overwritten with only the key-value pair remaining.
13. Increment an auhtor's age by 5.  
	`db.articles.update({title: 'B'}, {$inc: {'author.age': 5}})`
14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
	`db.articles.remove({_id: ObjectId("5d5c280962da9e9b5f997eb2")})`
Use sample.js data for below queries.

1. Find all males who play cricket.
	`db.users.find({$and: [{sports: {$in: ["cricket"]}}, {gender: {$eq: "Male"}}]})`
2. Update user with extra golf field in sports array whose name is "Steve Ortega".
	`db.users.update({name: {$eq: "Steve Ortega"}}, {$push: {sports: "golf"}})`
3. Find all users who play either 'football' or 'cricket'.
	`db.users.find({sports: {$all : ['football', 'cricket']}})`
4. Find all users whose name includes 'ri' in their name.
	`db.users.find({name: {$regex: /ri/}})`