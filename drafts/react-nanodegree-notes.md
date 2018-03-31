# React Fundamentals - Udacity React Nano-degree

Slack Office Hours
The React Slack channel is also important because one or more members of the Udacity team will hold Office Hours here. During office hours, we'll answer any and all questions you have, whether it's about the content, projects, services, or anything else related to React. These are generally held on Tuesday from 3pm-4pm PST, and on Friday from 10am-11am PST.
33
we've created an issue-reporting board.

——--

### 1 Why React

Composition is combining simple functions to make complex functions.
A good function should follow the "DOT" rule: Do One Thing

Examples

```javascript
function getProfileLink (username) {
 return 'https://github.com/' + username
}

function getProfilePic (username) {
 return 'https://github.com/' + username + '.png?size=200'
}
```
 to compose them, we'd just combine them together inside another function:


```javascript
function getProfileData (username) {
 return {
 pic: getProfilePic(username),
 link: getProfileLink(username)
 }
}
```

This function is doing a couple of different (however minor) things; it's creating two different URLs, storing them as properties on an object, and then returning that object. In the composed version, each function just does one thing:

`getProfileLink` – just builds up a string of the user's GitHub profile link
`getProfilePic` – just builds up a string the user's GitHub profile picture
`getProfileData` – returns a new object

Further Research
* [Compose me That: Function Composition in JavaScript](https://www.linkedin.com/pulse/compose-me-function-composition-javascript-kevin-greene)
* [Functional JavaScript: Function Composition For Every Day Use](https://hackernoon.com/javascript-functional-composition-for-every-day-use-22421ef65a10)


### Declarative Code

This is imperative code:

```javascript
const people = ['Amanda', 'Farrin', 'Geoff', 'Karen', 'Richard', 'Tyler']
const excitedPeople = []

for (let i = 0; i < people.length; i++) {
 excitedPeople[i] = people[i] + '!'
}
```
We're commanding JavaScript what to do at every single step. We have to give it commands to:

* set an initial value for the iterator - (let i = 0)
* tell the for loop when it needs to stop - (i < people.length)
* get the person at the current position and add an exclamation mark - (people[i] + '!')
* store the data in the ith position in the other array - (excitedPeople[i])
* increment the i variable by one - (i++)


this is declarative code:

```javascript
const excitedPeople = people.map(name => name + '!')
```

That's it! Notice that with this code we haven't:

* created an iterator object
* told the code when it should stop running
* used the iterator to access a specific item in the people array
* stored each new string in the excitedPeople array
...all of those steps are taken care of by JavaScript's .map() Array method.

React is Declarative!

```html
<button onClick={activateTeleporter}>Activate Teleporter</button>
```

Imperative code instructs JavaScript on how it should perform each step. With declarative code, we tell JavaScript what we want to be done, and let JavaScript take care of performing the steps.

Further Research
* Tyler's [Imperative vs Declarative Programming](https://tylermcginnis.com/imperative-vs-declarativ[-programming/) blog post
* [Difference between declarative and imperative in React.js?](https://stackoverflow.com/questions/33655534/difference-between-declarative-and-imperative-in-react-js) from StackOverflow

### Unidirectional Data Flow

In React, the data flows from the parent component to a child component.

If the child component needs to make a change to the data, then it would send the updated data to the parent component where the change will actually be made. Once the change is made in the parent component, the child component will be passed the data (that has just been updated!).

Now, this might seem like extra work, but having the data flow in one direction and having one place where the data is modified makes it much easier to understand how the application works.

### React is just JS

React builds on a lot of the techniques of functional programming.

Two JavaScript functions that are vital to functional programming that we should look at. 

* `.map()`
  * called on an existing array
  * returns a new array based what's returned from the function that's passed as an argument

```javascript
const names = ['Karen', 'Richard', 'Tyler'];
const nameLengths = names.map( name => name.length );
```

nameLengths will be a new array [5, 7, 5]

For a deeper dive, check out .map() [on MDN.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)


* `.filter()`
the function passed to .filter() is used as a test, and only items in the array that pass the test are included in the new array

### Summary

why React is great:

* compositional model
* declarative nature
* the way data flows from parent to child
* React is really just JavaScript
For further reading, feel free to check out the following:

[Virtual DOM](https://facebook.github.io/react/docs/optimizing-performance.html#avoid-reconciliation) from the React Docs. The Virtual DOM reflects a tree in which each node is an HTML element. React is able to traverse and carry out operations on this Virtual DOM, saving our app from having "costly" activity on the actual DOM.

[The Diffing Algorithm](https://facebook.github.io/react/docs/reconciliation.html#the-diffing-algorithm) from the React Docs. Diffing determines how to make efficient changes to the DOM. With diffing, old DOM nodes are taken out and replaced only when necessary. This way, our app doesn't perform any unnecessary operations to figure out when to render content.

-----

### Rendering UI with React

using React's .createElement()

`React.createElement( /* type */, /* props */, /* content */ );`

Let's break down what each item can be:

>type – either a string or a React Component
>
>This can be a string of any existing HTML element (e.g. 'p', 'span', or 'header') or you could pass a React component (we'll be creating components with JSX, in just a moment).
>
>props – either null or an object
>
>This is an object of HTML attributes and custom data about the element.
>
>content – null, a string, a React Element, or a React Component
>
>Anything that you pass here will be the content of the rendered element. This can include plain text, JavaScript code, other React elements, etc.

Virtual DOM = objects that describe real DOM nodes
`ReactDOM.render()` creates the actual DOM elements

[all supported html attributes](https://facebook.github.io/react/docs/dom-elements.html#all-supported-html-attributes)

Components - reusable pieces of code ultimately responsible for returning HTML to be rendered onto the page

there is only one method that is absolutely required in any React component class: `render()`

React is only concerned with the View layer of our app. This is what the user sees and interacts with

Components represent the modularity and reusability of React. You can think of your component classes as factories that produce instances of components. These component classes should follow the single responsibility principle and just "do one thing". If it manages too many different tasks, it may be a good idea to decompose your component into smaller subcomponents.

Further Research:

[Rendering Elements](https://facebook.github.io/react/docs/rendering-elements.html) from the React docs

------



test jsx must return a single element

const message = (
 <h1>All About JSX:</h1>
 <ul>
 <li>JSX</li>
 <li>is</li>
 <li>awesome!</li>
 </ul>
);