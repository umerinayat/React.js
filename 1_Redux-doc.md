# React State Management Using Redux ( redux flow )

## Redux has 3 Core Principles

1: One immutable store

Application sate is placed in a **single immutable store**.

- By immutable means state can not be changed directly.
- Having one immutable store:
  - Aids debugging
  - Support server side rendering
  - And makes things like undo / redo easly possible.

2: Actions trigger changes

In Redux the only way to change the state is to emit an **Action**

- Action describe the user intent for example a user might click sumbit contact form button, and that would trigger a **SUBMIT_CONTACT_FORM** Action

```
Example
action:
{
   type: SUBMIT_CONTACT_FORM,
   message: "Hi."
}
```

3: Reducers update the state

State changes are handle by **pure functions** and these functions are called reducers.

What is a Pure Function?
<https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976>

---

## Installing Redux:

1. `npm install redux`
2. `npm install react-redux`
3. `npm install redux-thunk or npm install redux-saga`
4. `npm install redux-immutable-state-invariant --save-dev`

---

## Initial Redux Setup Steps:

1. Create action
2. Create reducer
3. Create root reducer
4. Configure store
5. Instantiate store
6. Connect component
7. Pass props via connect
8. Dispatch action

## Adding more featuers to redux after intital setup involve 4 steps:

1. Create Action
2. Enhance reducer
3. Connect component
4. Dispatch action

---

# Creating a folder structure for keeping the redux related code files

<ul>
    <li>
        src ( folder )
        <ul> 
            <li> 
                redux ( folder )
                <ul> 
                    <li> 
                        actions ( folder contains actions code files that in turn contains action creators )
                        <ul> 
                            <li> taskActions.js ( file hold task related action creators ) </li>
                        </ul>
                    </li>
                    <li> 
                        reducers ( folder contains reducers function that handles the actions )
                        <ul> 
                            <li> taskReducer.js ( file: Reducer function that accpets the sate and action and returns a new state ) </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </li>
</ul>

# Using redux inside react components:

```javascript
import React from "react";

class TasksPage extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      task: {
        title: "",
      },
    };
  }
}
```
