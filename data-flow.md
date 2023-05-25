1.𝙥𝙖𝙧𝙚𝙣𝙩 𝙩𝙤 𝙘𝙝𝙞𝙡𝙙:

- 1st.child code (in 'ChildComponent.js'):

```javascript
const ChildComponent = (props) => {
  return <>{props.key1}</>
}
export default ChildComponent
```

- 2nd.parent code (in 'ParentComponent.js'):

```javascript
import ChildComponent from './ChildComponent.js'

const ParentComponent = () => {
  const data = {
    key1: value1,
    key2: value2,
  }

  return (
    <>
      <ChildComponent value={{ ...data }} />
    </>
  )
}
export default ParentComponent
```

2.𝙘𝙝𝙞𝙡𝙙 𝙩𝙤 𝙥𝙖𝙧𝙚𝙣𝙩 (use 'useContext' to pass data):

- 1st.child code (in 'ChildComponent.js'):

```javascript
import React, { useState, useContext } from 'react'

const initialData = {
  key1: value1,
  key2: value2,
}

const ChildrenContext = React.createContext()

const ChildrenProvider = ({ children }) => {
  const [data, setData] = useState(initialData)
  return (
    <ChildrenContext.Provider value={{ ...data }}>
      {children}
    </ChildrenContext.Provider>
  )
}

const useChildrenContext = () => {
  return useContext(ChildrenContext)
}

export { initialData, ChildrenProvider, useChildrenContext }
```

- 2nd.in 'index.js'

```javascript
import { ChildrenProvider } from './ChildComponent.js'

root.render(
  <React.StrictMode>
    <AppProvider>
      <App />
    </AppProvider>
  </React.StrictMode>
)
```

- 3rd.parent code (in 'ParentComponent.js'):

```javascript
import { useChildrenContext } from './ChildrenContext.js'

const ParentComponent = () => {
  const { key1, key2 } = useChildrenContext()

  return <h1>{key1}</h1>
}

export default ParentComponent
```

3.𝙘𝙝𝙞𝙡𝙙 𝙩𝙤 𝙥𝙖𝙧𝙚𝙣𝙩 (use 'useReducer' to change and pass part of data):

- +1st.'action.js'(if not, action will not work between files, since it's string instead of a variable???)

```javascript
export const ACTION_01 = 'ACTION_01'
```

- +2nd.'reducer.js'

```javascript
import {ACTION_01} from './action.js'

const reducer = (data, action) => {
		if (action.type=== ACTION_01) => {
				return {
						...data,
						key1: value3,
				}
		}
		throw new Error(`Not found action ${action.type}`)
}
export default reducer
```

- 3rd.child code (in 'ChildComponent.js'):

```javascript
import React, { useState, useContext, useReducer } from 'react'
import reducer from './reducer.js'
import { ACTION_01 } from './action.js'

const initialData = {
  key1: value1,
  key2: value2,
}

const ChildrenContext = React.createContext()

const ChildrenProvider = ({ children }) => {
  // const [data, setData]= useState(initialData) //-
  const [data, dispatch] = useReducer(reducer, initialData) //+
  const displayAction = () => {
    return dispatch({ type: ACTION_01 })
  } //+

  return (
    <ChildrenContext.Provider value={{ ...data, displayAction }}>
      {children}
    </ChildrenContext.Provider>
  ) //+'dispatchAction'
}

const useChildrenContext = () => {
  return useContext(ChildrenContext)
}

export { initialData, ChildrenProvider, useChildrenContext }
```

- 4th.in 'index.js'

```javascript
import { ChildrenProvider } from './ChildComponent.js'

root.render(
  <React.StrictMode>
    <AppProvider>
      <App />
    </AppProvider>
  </React.StrictMode>
)
```

- 5th.parent code (in 'ParentComponent.js'):

```javascript
import { useChildrenContext } from './ChildrenContext.js'

const ParentComponent = () => {
  const { key1, key2, displayAction } = useChildrenContext()

  return (
    <h1>
      {key1}
      {displayAction()}
    </h1>
  )
}

export default ParentComponent
```
