#### write commands for following mongodb opertaions

1. create a database named `sports`
	`use sports`

2. list all databases present in local mongod server.
	`show dbs`

3. create 3 collections named `cricket`, `football`, `TT` in sports database.
	`db.createCollection('cricket')`
	`db.createCollection('football')`
	`db.createCollection('TT')`


4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.
	`db.cricket.insertMany([{name: 'Shivam', age: 23, email: 'shivam@xyz.com', state: 'Punjab', auction_price: 100}, {name: 'Yash', age: 24, email: 'yash@xyz.com', state: 'Gujrat', auction_price: 90}, {name: 'Chetan', age: 21, email: 'chetan@xyz.com', state: 'Rajastan', auction_price: 80}])`

	`db.football.insertMany([{name: 'Prateek', age: 20, email: 'prateek@xyz.com', state: 'Rajasthan', auction_price: 70}, {name: 'Abhinav', age: 23, email: 'abhinav@xyz.com', state: 'UP', auction_price: 60}, {name: 'Tejas', age: 24, email: 'tejas@xyz.com', state: 'Karnataka', auction_price: 50}])`

	`db.TT.insertMany([{name: 'Shivam', age: 23, email: 'shivam@xyz.com', state: 'Punjab', auction_price: 100}, {name: 'Shreyansh', age: 20, email: 'shreyansh@xyz.com', state: 'Delhi NCR', auction_price: 40}, {name: 'Kennady', age: 25, email: 'kennady@xyz.com', state: 'Arunachal', auction_price: 30}])`

5. list all collections in sports database.
	`show collections`

6. rename `TT` collection to `tennis`.
	`db.TT.renameCollection('tennis')`

7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?
  	`db.createCollection('khokho', {capped: true, size: 2048, max: 3})`

8. check whether a collection is capped or not?
	`db.khokho.isCapped()`

9. remove all documents from `football` collection.
	`db.football.remove({})`

10. delete cricket collection completely.
	`db.cricket.drop()`
11. rename database sports to games
	`db.copyDatabase('sports', 'games')`
	`use sports`

12. delete sports database. 
	`db.dropDatabase()`