# Router

It is a package that allows react to make and change components according to the link the current user is in.

# Table of contents

- [Router](#router)
- [Table of contents](#table-of-contents)
- [Setup](#setup)
- [Components](#components)
  - [BrowserRouter](#browserrouter)
  - [Route](#route)
  - [Switch](#switch)
- [Navigation](#navigation)
  - [Redirect](#redirect)
  - [Link](#link)
  - [NavLink](#navlink)

# Setup

1.  install react router.(Run `yarn add react-router-dom` in terminal)
2.  It is used in **App.js** file in components folder.

# Components

## BrowserRouter

A Router that uses the HTML5 history API (pushState, replaceState and the popstate event) to keep your UI in sync with the URL.

* Examples
  ```jsx
  import { BrowserRouter } from "react-router-dom";
  <BrowserRouter>
    <App />
  </BrowserRouter>;
  ```

## Route

This component allows us to show what is the route link and the component to show when the link is visited.

* Parameters

  * **component**: This tells which component to load.
  * **render**: This is similar to component but when you want to add props to the component or run some code before redering the component.
  * **path**: This tells the link which has to be visited.
  * **exact**: This tells the router to create the component only if the link is matched exactly.

* Examples

  ```jsx
  import { Route } from 'react-router-dom';

  // when location = { pathname: '/about' }
  <Route path='/about' component={About}/> // renders <About/>
  <Route path='/contact' component={Contact}/> // renders null
  <Route component={Always}/> // renders <Always/>
  <Route path="/" component={Index}/> // renders <Index/>
  <Route exact path="/" component={Index}/> // renders null

  //To give extra props
  <Route
    path='/about'
    render={(props) => <About {...props} extra={someVariable} />}
  />
  // WRONG WRONG
  <Route
    path='/contact'
    component={(props) => <Contact {...props} extra={someVariable} />}
  />
  ```

## Switch

This component allows us to ensure exclusivity among the paths.It renders the first child **Route** or **Redirect** that matches the location.

* Example

  In the following example, when going to **/about**, without switch it will render the components, **About**,**User**,**NoMatch**.

  ```jsx
  import { Switch, Route } from 'react-router'

  <Switch>
    <Route exact path="/" component={Home}/>
    <Route path="/about" component={About}/>
    <Route path="/:user" component={User}/>
    <Route component={NoMatch}/>
  </Switch>
  ```

# Navigation

## Redirect

This component will navigate to a new location or link.

* Parameters

  * **from**: The URL to redirect to.
  * **to**: A pathname to redirect from.

* Examples

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

## Link

Provides declarative, accessible navigation around your application.

* Parameter

  * **to(String)**: the link to goto.
  * **to(Object)**: the link with parameters to the link. The keys
    * **pathname**: A string representing the path to link to.
    * **search**: A string represenation of query parameters. \* **hash**: A hash to put in the URL, e.g. #a-hash.

* Examples

  ```jsx
  import { Link } from 'react-router-dom';

  <Link to="/about">About</Link>

  <Link to={{
    pathname: '/courses',
    search: '?sort=name',
    hash: '#the-hash'
  }}/>
  ```

## NavLink

A special version of the **Link** that will add styling attributes to the rendered element when it matches the current URL.

* Parameter

  * **to**: Similar to [Link](#navigation-link)
  * **activeClassName**: The classname that must be assigned when the url is same.(DEFAULT: `active`)
  * **activeStyle(Object)**: In case you want to style it directly
  * **exact(bool)**: This is similar to exact in [Route](#components-route)

* Examples

  ```jsx
  import { NavLink } from 'react-router-dom'

  <NavLink to="/about">About</NavLink>

  <NavLink
    to="/faq"
    activeClassName="selected"
  >FAQs</NavLink>

  <NavLink
    to="/faq"
    activeStyle={{
      fontWeight: 'bold',
      color: 'red'
    }}
  >FAQs</NavLink>
  ```
