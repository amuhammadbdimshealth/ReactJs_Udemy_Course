# Section-7 | Deeper Dive Into Components And React Internals

## S7-L102 | Ref

---

### Old way of creating Ref And Using It

```Jsx
class Person extends Component {
  constructor(props) {
    super(props);
    console.log("[Person.js] Inside Constructor", props);
  }
  componentDidMount() {
    // Using the Reference to focus the input element
+    if (this.props.position == 0) this.inputElement.focus();
  }
  render() {

    return (
      <Aux>
        //...

        // This creates a reference to the input element and assigns it to the class property `inputElement` which is created on the fly. This can then be used elsewhere to focus the element. See the  `componentDidMount()` method.

         <input
+          ref={inp => {
            this.inputElement = inp;
          }}
          type="text"
          onChange={this.props.changed}
          value={this.props.name}
        />
      </Aux>

    );
  }
}

```

### New Way of creating Ref And Using It

```Jsx
class Person extends Component {
constructor(props) {
    super(props);
    console.log("[Person.js] Inside Constructor", props);

    // Creating Reference
+    this.inputElement2 = React.createRef();
  }
  componentDidMount() {
     // Using the Reference to focus the input element
+    if (this.props.position == 1) this.inputElement2.current.focus();
  }
  render() {

    return (
      <Aux>
        //...

        // This creates a reference to the input element and assigns it to the class property `inputElement` which is created on the fly. This can then be used elsewhere to focus the element. See the  `componentDidMount()` method.

         <input
+          ref={this.inputElement2}
          type="text"
          onChange={this.props.changed}
          value={this.props.name}
        />
      </Aux>

    );
  }
}

```

## S7-L104 | The Context API

---

### Objective

Pass some global data through the component tree

### Solution

1. Pass the data by passing down props
2. Use the Context API

### The Context API

- Context provides a way to pass data through the component tree without having to pass props down manually at every level.

- In a typical React application, data is passed top-down (parent to child) via props, but this can be cumbersome for certain types of props (e.g. locale preference, UI theme) that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.

#### Code - Context API

1. We will pass the authentication state from App.js to _Person.js_ using Context API.
   _App.js_ will provide the context while the _Person.js_ will Consume the Context

    _App.js_

    ```js
    /* The Context API is really great for global settings .
    The createContext() function below creates a Component we can use in JSX
    */
    export const AuthContext = React.createContext(false);

    class App extends Component {
    //...

    render() {
        return (
        /*
                * So now we're wrapping all components where we plan on extracting that value from the context with a special component, the AuthContext component.

                * So now we're providing this context to all child components in there, no matter on which level they are
                */

        <AuthContext.Provider value={this.state.authenticated}>
            {persons}
        </AuthContext.Provider>
        );
    }
    }
    ```

2. Using the Context in _Person.js_

    _Person.js_

    ```jsx
    //...other imports
    import { AuthContext } from "../../../containers/App";

    class Person extends Component {
        render() {
            return (

                <AuthContext.Consumer>

                    {/* {this.props.authenticated ? <p>I am authenticated</p> : null} */}

                    {/* This method receives one argument and this is the data we're passing down with the context,this could of course be an object, in our case it's a boolean. So here it's our auth state and we return the jsx we want to render. */}

                    {/* and we can pass data around without having to set up this chain of props. */}

                    {auth => (auth ? <p>I am authenticated</p> : null)}

                </AuthContext.Consumer>;
            );
        }
    }

    ```

## S7-L104 | More On The Context API

---

The basic that you have learnt above is enough for now. See the link below when you revise the advanced and a more modern usage of context.

[Lecture Link Here](https://www.udemy.com/react-the-complete-guide-incl-redux/learn/v4/t/lecture/12296822?start=0)

Check the code for lecture `S7-L105-Context`


## S7-L106 | Upddated Life Cycle Hooks

---

1. Avoid the following life-cycle hooks : 
    1. componentWillMount()
    2. componentWillUpdate()
    3. componentWillReceiveProps

2. Newly Added Hooks
    1. getDerivedStateFromProps
    2. getSnapshotBeforeUpdate - Used in cases where we need to return to the previous scrolling position. See the example [Here!](https://reactjs.org/docs/react-component.html#getsnapshotbeforeupdate)


3. Check the diagram link below as a cheat sheet of life cycle hooks

    [Lifecycles](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## S7-L107 | The "memo" Method(16.4)

---

### React.PureComponent

* React.PureComponent is similar to React.Component. The difference between them is that React.Component doesn’t implement shouldComponentUpdate(), but React.PureComponent implements it with a shallow prop and state comparison.

* If your React component’s render() function renders the same result given the same props and state, you can use React.PureComponent for a performance boost in some cases.

### React.memo

```js
const MyComponent = React.memo(function MyComponent(props) {
  /* render using props */
});
```

* React.memo is a higher order component. It’s similar to React.PureComponent but for function components instead of classes.

* If your function component renders the same result given the same props, you can wrap it in a call to React.memo for a performance boost in some cases by memoizing the result. This means that React will skip rendering the component, and reuse the last rendered result.

* By default it will only shallowly compare complex objects in the props object. If you want control over the comparison, you can also provide a custom comparison function as the second argument.

```js
function MyComponent(props) {
  /* render using props */
}
function areEqual(prevProps, nextProps) {
  /*
  return true if passing nextProps to render would return
  the same result as passing prevProps to render,
  otherwise return false
  */
}
export default React.memo(MyComponent, areEqual);

```


* Note

    Unlike the shouldComponentUpdate() method on class components, the areEqual function returns true if the props are equal and false if the props are not equal. This is the inverse from shouldComponentUpdate.