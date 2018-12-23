# Previous Pathname Middleware

## Description

Adds the previous pathname to router in redux store.

## Usage

In store:

```javascript
import { createStore, compose, applyMiddleware } from "redux"
import { routerMiddleware } from "connected-react-router"
import previousPathnameMiddleware from "@alexseitsinger/previous-pathname-middleware"

import createRootReducer from "../reducer"

function configureStore(history, initialState = {}) {
	const rootReducer = createRootReducer(history)
	const middleware = [previousPathnameMiddleware, routerMiddleware(history)]
	const storeEnhancers = compose(applyMiddleware(...middleware))
	const store = createStore(rootReducer, initialState, storeEnhancers)
	return store
}
```

In component:

```javascript
import React from "react"
import PropTypes from "prop-types"
import { connect } from "react-redux"

function App({ previousPathname }) {
	return <div>App</div>
}

App.propTypes = {
	previousPathname: PropTypes.string.isRequired
}

const mapStateToProps = (state) => {
	return {
		previousPathname: state.router.previousPathname
	}
}

export default connect(mapStateToProps)(App)
```
