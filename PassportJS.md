# PassportJS
## Installation
Install using ```yarn add passport <passport strategy>``` on the terminal

---

**NOTE**:
using google from now on

---
## Setup with strategy
```javascript
const passport = require('passport')
const googleStrategy = require('passport-google-oauth20')

passport.use(new googleStrategy({
		clientID: '',
		clientSecret: '',
		callbackURL: '/auth/google/callback' //user comes here after logging in
	}),
	// code going to come later for saving users
)
```
---

**NOTE**:
To get clientID and secret goto https://console.developers.google.com and search for google+ API and activate it, remember to give the correct callbackLink

---
## Storing keys
* Create a './config/keys.js' with the following code
	```javascript
	module.export = {
		googleClientID:
		googleSecret:
	}
	```
* add the file to .gitignore

## Showing login
```javascript
app.get('/auth/google',passport.authenticate('google',{
	scope:['profile','email']
}))
```

## Callback URL setup
```javascript
app.get('/auth/google/callback',passport.authenticate('google'))
```

## What to do on successful login
```javascript
passport.use(/*Strategy setup*/,
	(accessToken, refreshToken, profile, done)=>{
		//done called to continue like the following
		if(err)
			done(err)
		else
			done(null, data)
	}
)
```
## adding user to database
```javascript
// Create a User model
passport.use(/*Strategy setup*/,
	(accessToken, refreshToken, profile, done)=>{
		// Making sure 2 people with same google profile re not created
		User.findOne({googleId: profile.id})
			.then((existingUser)=>{
				if(existingUser){
					done(null, existingUser)
				}
				else{
					new User({googleId: profile.id}).save()
						.then(user=>done(null, user))
				}
			})
	}
)
```
## Showing person is logged
It is done using serializeUser and deserializeUser
```javascript
passport.serializeUser((user, done)=>{
	done(null, user.id)
})
```