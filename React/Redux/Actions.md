# Actions
It is used to do functions that might change the state of any of the components
## Setup
1. install redux thunk, ```yarn add redux-thunk```
2. import and add it as a middleware to redux in index.js of **src** directory.
	```javascript
	import reduxThunk from 'redux-thunk';
	...
	const store = createStore(reducers, {}, applyMiddleware(reduxThunk));
	...
	```
3. Create a folder called **actions** in **src** for the **action creator**.
4. Create 2 files called **index.js** and **types.js** into **actions** folder.
## Notes
* **types.js** will house names for each of the action names. Example:
	```javascript
	export const FETCH_USER = 'fetch_user';
	export const FETCH_PROFILE = 'fetch_profile';
	export const LOGOUT_USER = 'logout_user';
	```
* **index.js** will contain both all the types and the action creators for the components to import.
* Basic example of an **action creator**
	```javascript
	import {FETCH_USER} from './types.js';
	import axios from 'axios';
	export const fetchUser = () => async dispatch => {
		const res = await axios.get('/api/current_user');
		dispatch({type: FETCH_USER, payload:res.data});
	};
	```
## Using actions in components
* Basic setup
	```javascript
	import {connect} from 'react-redux';
	import * as actions from '../actions';
	...
	export default connect(null, actions)(App);
	```
* Now the action is available as props. Ex:
	```jsx
	const App = props =>	{
		return (<h1 onClick={props.fetchUser}>hello</h1>);
	}
	```
## Configuring it with reducers
inside authReducers.js in reducers folder,
```javascript
import {FETCH_USER} from '../action/types'
export default function(state=null, action){
	switch(action.type)	{
		case FETCH_USER:
			return action.payload||false;
		default:
			return state;
	}
}
```
## Getting the state in a component(FOR Reducers)
inside a component
```javascript
import {connect} from 'react-redux';
...
const mapStateToProps({ auth }){
	//whatever you return will be obtained as props to the component
	return { auth };
}
export default connect(null)(App);
```
