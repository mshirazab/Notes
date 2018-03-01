# MongoDB and Mongoose
## Connection with mongoDB
```javascript
const mongoose = require('mongoose');
const MONGO_URL = '';

mongoose.connect(MONGO_URL);
mongoose.connection
	.once('open',() =>{
		// code for success
	})
	.on('error', (error) =>{
		// code on error
	})
```
---

**NOTE**
Promises dont work by default use ```mongoose.Promise=global.Promise```

---
## Models
- importing
	```javascript
	const mongoose = require('mongoose');
	const Schema = mongoose.Schema;
	```
- making a Schema
	```javascript
	const UserSchema = new Schema({
		// The schema
	});
	```
- adding it to mongoDB
	```javascript
	mongoose.model('user', UserSchema);
	```

## Queries
### Adding Data
- Creating the data using the model created
	```javascript
	const User = require('mongoose').model('user');
	...
	const user = new User(/*DATA*/);
	```
- Save it
	```javascript
	user.save()
	```
### Finding
- finding many users
	```javascript
	User.find(/*search criteria*/)
		.then((users)=>{
			/* Do something with users */
		})
	```
	---

	**NOTE**
	This will be an array even if only one record is there

	---
- finding one user (first one)
	```javascript
	User.findOne(/*search criteria*/)
		.then((user)=>{
			/* Do something with users */
		})
	```
### Deleting
- delete many records
	```javascript
	User.remove(/*search criteria*/)
		.then(()=>{
			/* Do something with users */
		})
	```
	---

	**NOTE**
	remove() will not give your the deleted element

	---

