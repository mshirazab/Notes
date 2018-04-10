# Startup

* startup your project in terminal using 
	```bash
	$yarn init
	```
* add required dependencies using 
	```bash
	$yarn add express
	```
* setup in app.js
	```javascript
	const express = require('express')
	const app = express()
	module.exports = app
	```
* setup in index.js
	```javascript
	const app = require('./app')
	const port = process.env.PORT || 3050
	app.listen(port, ()=>{
		console.log(`Listening at port ${port}`)
	})
	```
# Testing
* install 2 packages
	```bash
	$yarn add mocha supertest nodemon --dev
	```
* make a **describe** and **it** which is given by mocha
	```javascript
	// it is used to check if it ran correctly
	const assert = require('assert') 

	describe('Heading message', () => {
		it('test message', (done) =>{
			// assert to check if it fine using 
			assert(1+1==2)
			//once the testing is done, call the done
			done()
		})
	})
	```
* in package.json,
	```json
	{
		...
		"scripts":{
			"test": "nodemon --exec 'mocha --recursive -R min'"
		}
		...
	}
	```
