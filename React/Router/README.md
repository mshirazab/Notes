# Router
It is a package that allows react to make and change components according to the link the current user is in.
## Table of contents
* Navigation
	* [redirect](#navigation-redirect)
## Setup
1. install react router.(Run ```yarn add react-router-dom``` in terminal).

## Usage
* It is used in **App.js** file in components folder.

## Components
1. [BrowserHistory](./BrowserHistory.md)
2. [Route](./Route.md)
3. [Switch](./Switch.md)

## Navigation
### <a name="navigation-redirect"></a>Redirect
This component will navigate to a new location or link.
#### <a name="navigation-redirect-parameters"></a>Parameters
* **from**: The URL to redirect to.
* **to**: A pathname to redirect from.

#### <a name="navigation-redirect-examples"></a>Examples
```jsx
import { Route, Redirect } from 'react-router'

<Route exact path="/" render={() => (
  loggedIn ? (
    <Redirect to="/dashboard"/>
  ) : (
    <Redirect to="/"/>
  )
)}/>
```
2. [NavLink](./NavLink.md)
3. [Redirect](./Redirect.md)