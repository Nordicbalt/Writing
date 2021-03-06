# Fast guide on the Todo App in React and Redux ⚛ ⏩

[<img src="https://images.unsplash.com/1/work-station-straight-on-view.jpg?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=" alt="https://unsplash.com/photos/xII7efH1G6o">](https://unsplash.com/photos/xII7efH1G6o) https://unsplash.com/photos/xII7efH1G6o


Building the Todo List Example with React and Redux. The official documentation is good, but sometimes it helps to have a quick overview.

See my [Github Repo](https://github.com/DDCSLearning/reduxTodo) for actual code (Using create-react-app, redux, [ducks](https://github.com/erikras/ducks-modular-redux)).

<img src="https://raw.githubusercontent.com/reactjs/redux/master/logo/logo.png" alt="react logo" height="200" align="right"/>
<img src="https://facebook.github.io/react/img/logo.svg" alt="react logo" height="200"/>


## 📄 Table of contents

  * [1. Before writing code](#1-before-writing-code)
  * [2. Write your basic components outlay](#2-write-your-basic-components-outlay)
  * [3. Get the state and actions right](#3-get-the-state-and-actions-right)
  * [4. Next: Reducers](#4-next-reducers)
  * [5. Store and Dispatching](#5-store-and-dispatching)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)




---

>"In the business world, the rearview mirror is always clearer than the windshield."
― [Warren Buffett](https://de.wikipedia.org/wiki/Warren_Buffett)

---


## 1. Before writing code

Think about what you want to achieve in your app.
As always [think in React](https://facebook.github.io/react/docs/thinking-in-react.html)! Have an idea how your app is structured with components. Also decide which components have a presentational function (mainly for presenting data) and which have a container function (providing data and behavior). Check [Dan Abramov's article](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.24ud80eei) for more.

## 2. Write your basic components outlay

Find the [code](http://redux.js.org/docs/basics/ExampleTodoList.html) of Facebook's example.

If that's already overwhelming start with the basics.

Cut down you need:
1. an input field with a button (AddTodo)
1. a list that renders the todo items (TodoList)
1. and additionally a filter component that shows your items accordingly (Filter)

## 3. Get the state and actions right
In previous articles we learned what `State` is all about. It's data that changes and cannot or should not be passed via props.
Also, remember `Actions` from Redux, which are information loads about events from user interaction.

Revisit your components and think about theirs State and Actions:
- AddTodo: No State is needed, since data doesn't change based on input. The components allows to add items - that's the action.
- TodoList: Needs 1 State for displaying an array of items and 1 state for rendering out accordingly to the filter. The action here is to display the status whether an item is completed or not.
- Filter: Needs State for rendering accordingly to the currently set filter. The action comes from clicking on a link to display other lists.

`ActionCreators` return an actual JavaScript object for your previously designed action-information-loads.


## 4. Next: Reducers

[Reducers](http://redux.js.org/docs/basics/Reducers.html) actually take the current State combine it with the actions and provide a new State.
Each action needs a corresponding reducer.
Be sure to put the reducer logic into container components to keep presentational components clean.

With reducers we have to:
- define the shape of State
- handle Actions
- and maybe split reducers

**Therefore:**

- The state has to be extended by an item when the addTodo action is called
- The state has to be reorganized when the filter action is called

## 5. Store and Dispatching

The Store brings actions and reducers together, and allows the state being updated with dispatching actions. You should only have one Store in your application.

For dispatching make use of container components.
>a container component is just a React component that uses store.subscribe() to read a part of the Redux state tree and supply props to a presentational component it renders.


- Displaying the list requires the container of TodoList to define a function that filters the items according to the filter variable. Return that function in `mapStateToProps` to transform Redux state into Props. Additionally we want to dispatch the action like `toggleTodo` with `mapDispatchToProps`. Finally the container will be created with `connect`, connecting the passed props to the presentational component.
- Create AddTodoForm as container needs the same steps for reading Redux state and dispatching an `onSubmit` function.
- The filter component needs the same steps for reading Redux state and dispatching an `onClick` function.

## Conclusion
As we can see the core concept and ideas are really simple. It's just hard to stay focused and not get lost in the syntax specific issues when creating redux apps.


```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

## Useful links & credits
- [🌐 "React" - Facebook (official site)](https://facebook.github.io/react/)
- [🌐 "Redux" - Facebook (official site)](http://redux.js.org/)
- [📄 "Build React apps using mocks" - rajaraodv (8min article)](https://medium.com/@rajaraodv/step-by-step-guide-to-building-react-redux-apps-using-mocks-48ca0f47f9a#.nyiqb1biq)
- [📄 "Ducks file structure for Redux" - S.C.Barrus (3min article)](https://medium.com/@scbarrus/the-ducks-file-structure-for-redux-d63c41b7035c#.305a6da9k)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
