## Components

```javascript
const MyCoolComponent = () => {

}
```

☝ This is what is known as a "stateless component" in React.
It uses an ES6 arrow function. As stateless component is simply a function of it's props.
Feed it some props and the resulting render will change accordingly.

--

```javascript
class MySuperComponent extends React.Component {
  render(){

  }
}
```

☝ This is a "statefull component" or "class component", it has something known as "state". State a
plain object representation of all the things that the component needs to be able to
change. A stateful component also has a "lifecycle", but more on that later. Every
statfull component will need a `render()` function, which determines what is output.

--

```javascript
const GreetingMessage = () => {
  <div className="hey-there">
    <p>Hello ExchangeJS</p>
  </div>
}
```

☝ This is JSX. It feels bad to mix (what looks like) HTML into your JavaScript at first,
but trust me, this is a really nice way to represent your DOM. There's no obligation in
React to use JSX, but there are few downsides. You can put normal HTML attributes on
JSX tags, except in a few cases where the attribute names collide with JavaScript keywords –
like the word `class`; so `className` has to be used instead.

--

```javascript
import GreetingMessage from './path/to/component'
export default const MyCoolComponent = () => {
  <div>
    <GreetingMessage />
  </div>
}
```

☝ Components are meant to be composable, so you should probably export them to allow this
to happen. Doing that means you can import them and use them in other components.


## Props

```javascript
import GreetingMessage from './path/to/component'
export default const MyCoolComponent = () => {
  <div>
    <GreetingMessage text="Hello ExchangeJS" />
  </div>
}
```

Components can be passed props, which can be used to determine their output. Passing props
looks a lot like defining attributes in HTML. Here we pass "Hello ExchangeJS" in a prop
called `text`

--

```javascript
const GreetingMessage = (props) => {
  <div className="hey-there">
    <p>{ props.text }</p>
  </div>
}
```

Components receive props through the first argument in it's function definition. The argument
is an object containing all of the props passed to the component. You can use them in your
component how you see fit.

--


```javascript
GreetingMessage.propTypes = {
  text: React.propType.string.required,
}
```

Defining the `propTypes` of a component is important, because it can help restrict the type
of data your component accepts. You'll get an exception if you send it the wrong props, but
the definition is up to you.

--

```javascript
GreetingMessage.defaultProps = {
  text: 'Hello world',
}
```

`defaultProps` is a place where you can define the values of your component's props if they
are not passed in by a parent component.

## State

```javascript
class MyApp extends React.Component {
  render(){
    setTimeout( ()=> {
      this.setState({ greeting: 'Hello ExchangeJS!'})
    }, 2000)

    <div>
      <GreetingMessage text={ this.state.greeting } />
    </div>
  }
}
```

Most of the time its better to use stateless components, but occasionally you'll need a
component that can control it's own state. In the component above we're updating the text
sent to our `GreetingMessage` component 2 seconds after the first render. This will also
trigger a re-render of the GreetingMessage component, since it's props will have changed.

--

```javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      greeting: 'Hi there'
    }
  }

  render(){
    <div>
      <GreetingMessage text={ this.state.greeting } />
    </div>
  }
}
```

You can definte the initial state before rendering occurs by defining a class constructor.
If you define a class constructor, you'll need to pass props to a call to `super` before
adding anything else to the constructor.
