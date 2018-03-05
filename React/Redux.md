# Redux
## Setup 
* inside index.js
	```javascript
	import {Provider} from 'react-redux';
	import {createStore, applyMiddleware} from 'redux'
	...
	const store = createStore(/*reducers*/, /*initial state*/, applyMiddleware())
	...
	ReactDOM.render(
		<Provider store={store}>
		<App/>
		</Provider>
		,/*location*/
	)
	```
* create a reducers folder and a file index.js inside it.
* create a file for each reducer
	```javascript
	export default function(state={/*inital state*/}, action)	{
		switch(action.type)	{
			default:
				return state;
		}
	}
	```
* In index.js of reducers
	```javascript
	import {combineReducers} from 'redux';
	import /*the reducer*/;
	export default combinerReducers({
		/*name of reducer*/:/*the reducer*/,
		auth: authReducer //example
	})
	```
* add the reducer to index.js
	```javascript
	import /*path to reducers*/
	import reducers from './reducers'; //example
	...
	const store = createStore(reducers, /*initial state*/, applyMiddleware())
	```