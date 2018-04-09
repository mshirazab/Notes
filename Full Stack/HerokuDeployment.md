# NodeJS Heroku Deployment
## Deployment Checklist
### Dynamic Port Binding
In app.js where you express.listen()
```javascript
...

const PORT = process.env.PORT || 5000; // process.env is given by heroku
app.listen(PORT);

...
```
### Specify Node Environment
In package.json
```json
{
	...

	"engines":{
		"node": "8.1.1",// the version you want to run
		"npm": "5.0.3"
	},
	
	...
}
```
### Specify start script
In package.json, edit start in scripts
```json
{
	...
	
	"start":{
		"start": "node index.js"
	},
	
	...
}
```
### create .gitignore file
Create a .gitignore in root directory
```
node_modules
dev.js
```

## First deployment
* Create an account in heroku account at https://www.heroku.com
* Install git at https://git-scm.com/downloads
* run in terminal the following code
	```bash
	$git add .
	$git commit -m "My message"
	```
* Download Heroku CLI https://devcenter.heroku.com/articles/heroku-cli
* login to heroku ```heroku login```
* Create app at heroku and it will help you after that by giving a git link
* ```heroku git:remote -a <The app name>```
* ```git push heroku push```
* run ```heroku open``` to open the website
* run ```heroku logs``` to check problems 

## Subsiquent Deploys
* ```git push heroku push```

## Adding sensitive data
* goto app console n heroku website
* then settings and add them as config vars
* then you can access them with ```process.env```