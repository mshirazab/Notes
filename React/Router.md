# Router
## Checklist
* make sure you install **react-router-dom**
* import the following
	```javascript
	import {BrowserRouter, Route} from 'react-router-dom'
	```
## Notes
* done in app.js
* basic setup
	```jsx
	<BrowserRouter>
	// Only one child is allowed
	<div>
		//Here you can write components that must be shown at all times
		<Route exact path="/" component={/*component_name*/} />
		//Example
		<Route exact path="/" component={App} />		
	</div>
	</BrowserRouter>
	```
* ```exact={true}``` tells Route to not stack the link, it is essential so as not to get wierd outputs.