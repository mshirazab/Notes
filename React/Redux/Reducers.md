# Redux
They store the state and actually change the data of the state when an action invokes it.
## Setup 
1. create a **reducers** folder and a file **index.js** inside it.
2. create a file for each reducer. Ex: in **reducers/authReducer.js**
	```javascript
	import {FETCH_USER} from '../action/types';
	export default function(state=null, action){
		switch(action.type)	{
			case FETCH_USER:
				return action.payload||false;
			default:
				return state;
		}
	}
	```
3. In index.js of reducers
	```javascript
	import {combineReducers} from 'redux';
	import /*the reducer*/;
	export default combinerReducers({
		/*name of reducer*/:/*the reducer*/,
		auth: authReducer //example
	})
	```
4. inside a component
	```javascript
	import {connect} from 'react-redux';
	...
	const mapStateToProps({ auth }){
		//whatever you return will be obtained as props to the component
		return { auth };
	}
	export default connect(null)(App);