# Redux
It allows global state for our react Application

## How it achieves this
1. A **component** calls an action creator.
2. This action creator responsible for doing some data request or some function that might cause the state to change.
3. Once it is done, we use **redux-thunk** to dispatch an action to **reducers**.
4. Reducers change some flag(**store**) to notify results.
5. The components can use the results to change state or something like that(**REPEAT**).

## Setup
1. install dependencies ```yarn add redux react-redux```.
2. Configure the index.js file in **src** to accept redux.
	```javascript
	import {Provider} from 'react-redux';
	import {createStore, applyMiddleware} from 'redux'
	import reducers from './reducers';
	...
	const store = createStore(reducers, {}, applyMiddleware())
	...
	ReactDOM.render(
		<Provider store={store}>
		<App/>
		</Provider>
		,document.find("#root")
	)
	```
## Links to do them
---

**NOTE**
The examples create a redux cycle which checks whether a user is signed in or not.

---
* [Reducers](./Reducers.md) (have to do actions/values.js first)
* [Actions](./Actions.md)