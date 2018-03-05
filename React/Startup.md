# Startup
## Installing create-react-app
```bash
yarn global add create-react-app
```
## Creating the app
```bash
create-react-app client
```
---

**NOTE**
it will create a folder called **client** which has the react boilerplate.

---
## Combining Express app and react
* Install concurrently
	```bash
	yarn add concurrently --dev
	```
* add in package.json in server directory
	```json
	{
		"scripts":{
			"server": "node server.js",
			"client": "npm start server --prefix client",
			"dev": "concurrently \"npm run server\" \"npm run client\""
		}
	}
	```
* add in package.json in client directory
	```json
		{
			"proxy":{
				"/auth/google":"http://localhost:5000"
			}
		}
	```
## Add redux and routing
```bash 
$yarn add redux react-redux react-router-dom
```