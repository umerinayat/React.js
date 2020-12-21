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
In Redux Reducer is just a function that accepts the **current state** and **action**,and it returns a new state.

What is a Pure Function?
<https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976>

## Redux has uni-directional data flow:

- Data flows down
- Actions flows up

```
→ Action
|   ↓
| Store <-> Reducers
|   ↓
← React  (Note: React components connected to store using redux related lib called react-redux)
```

---

## Installing Redux:

1. `npm install redux`
2. `npm install react-redux`
3. `npm install redux-thunk or npm install redux-saga`
4. `npm install redux-immutable-state-invariant --save-dev`

---

# Actions, Store, and Reducers

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

---

# Introducing Redux Saga

## What is Redux Saga?

- Redux Middleware
- Consumes actions, dispatches actions and side-effects
- Maintains continously running processes called sagas.

Redux Saga is the **Redux Middleware**. That means it needs to be added to a Redux store in the middleware chain for it to have any effect.

Once it has been added as middleware, it consumes the actions that come out of your application. In response it accasionally dispatches other actions or create side effects. Side effects includes interactions with databases with outside API's etc.

Unlike Other middlewares, like Redux Thunk, Redux-saga maintains continously running processes called sagas to manage the logic of the application. Using these sagas effectively is a large part of what using redux is all about.

## What is Saga?

What is a saga? The word saga has many different definitions, even within the world of computer programming .Let's have a look at one or two. So, a saga in general functional programming is a series of reversible transactions. Sagas were designed to replace single huge locking transactions. For example, a deposit to a bank would require changing various different spreadsheets. The traditional way would involve locking all these spreadsheets, changing a value, then unlocking them, whereas with a functional programming saga, you would break the transaction into small steps, and if there was an error anywhere along the way, you would reverse all the steps that you've taken. Now to manage all this, sagas use a process manager to keep track of what's been done and what other actions need to be taken. Now, Sagas in Redux are quite a bit different. So in redux-saga, sagas are more characterized by their long running‑ness than their reversibility. Things done by redux-saga can be reversed, but there's little mention of reversal in the redux-saga docs, and in practice, it's not something that happens too often. Rather, a saga is a process that runs in the background that creates side effects for your application. One unique thing about sagas that we'll be exploring thoroughly is that they're made with ES6 generator functions. There are many reasons for this, but the simplest one is that ES6 generators and yield result in better, more maintainable, and more concise code. Like functional sagas, redux-saga also has a process manager, but that process manager is redux-saga itself. The various sagas that you have running all communicate with redux-saga, and redux-saga stops or starts the various processes as is appropriate. So to summarize, here's what sagas actually do. They listen for actions and then dispatch other actions. They dispatch actions and listen for them using tools called effects. In an upcoming module, we'll be exploring every effect that redux-saga has to offer. In addition, sagas can modify external APIs or change system files or access databases. In your Redux application, all of this side effect functionality should be isolated in your sagas. In the next clip, we'll answer the question why you should use redux-saga.

# Why Use Redux Saga?

So at this point, you may be wondering why should I even use redux‑saga? Isn't Redux Thunk or just middleware enough for my use cases? Let's have a look at some of the rationale. So redux‑saga makes side effects easy. Almost all side effects require some sort of asynchronous functionality, and since redux‑saga uses yield and generators, you can often get this asynchronous functionality in a clearer and more concise way than without them. In addition, redux‑saga has many advanced tools that cover almost all real‑world use cases. For example, using redux‑saga, you can fork a process into several different processes or stop a process so that another process can run. Finally, redux‑saga is quite sophisticated, it has way more features than Redux Thunk, which is just a simple connector. When you get down to it, Redux Thunk lets us solve a lot of problems with our Redux application, but it encourages a lot of bad coding practices like putting a lot of logic inside your action creators. Redux‑saga offer solutions to these problems that are much better. The trade off is that redux‑saga is more complicated and takes longer to learn. In the next clip, we'll have a direct comparison of the two libraries.

# Redux Thunk vs. Redux Saga

The most obvious comparison you can make with redux‑saga and any other library is between it and Redux Thunk. These are the two main Redux middlewares, and it wouldn't be surprising if in your workplace or business you have the discussion, should we use Redux Thunk or redux‑saga in this application that we're building? Now, personally, I believe almost all cases call for redux‑saga, but let's have a closer look. So Redux Thunk is a common middleware used in many Redux applications. So is redux‑saga. In this sense, they're very similar. Redux Thunk was created by the original creator of Redux, Dan Abramov. Two, as we mentioned earlier, solve necessary issues with the structure of a Redux app, like how to deal with side effects. On the other hand, redux‑saga was created by a third‑party developer. They did so because the use cases provided by Redux Thunk and existing middlewares simply didn't match their needs. Redux Thunk doesn't use any special JavaScript contacts, and you can throw it into almost any application that's already running Redux. On the contrary, Redux‑saga uses more advanced structures like generators and yield and only works in environments that support that. Now, lately, yield support has gotten a lot better. So in environments like Chrome, you can use it without any precompilation. However, you're always going to be more limited choosing redux‑saga than Redux Thunk. Redux Thunk doesn't really have any built‑in ways to manage asynchronous calls. If you have to make an asynchronous call and wait for its response and then make another call and another call, you're stuck with either a pyramid of callbacks or a chain of .thens. On the other hand, redux‑saga is designed to leverage yield and generators to make asynchronous simple. I can't really stress enough how much easier it is to do async after you master generators, yield, and redux‑saga. We'll be doing so in a large number of demo videos that are coming up in an upcoming module. Finally, if you have multiple different thunks for doing different things, there's no way to organize side effects between them. At best, you need to create some kind of cross‑channel communication or create a different thunk for every tiny action you want to do. On the other hand, redux‑saga is well designed for having a lot of sagas running in parallel. You use effects to communicate between sagas and tell a redux‑saga to stop one and start the other. All right, in the next clip, we'll be setting the application up.
