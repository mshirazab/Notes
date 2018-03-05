# Redux
It allows global state for our react Application

---

**NOTE**
The examples create an action creator which checks whether a user is signed in or not.

---
## How it achieves this
1. A **component** calls an action creator.
2. This action creator responsible for doing some data request or some function that might cause the state to change.
3. Once it is done, we use **redux-thunk** to dispatch an action to **reducers**.
4. Reducers change some flag(**store**) to notify results.
5. The components can use the results to change state or something like that(**REPEAT**).

## Installation
```bash 
$yarn add redux react-redux
```
## Links to do them
* [Actions](./Actions.md)