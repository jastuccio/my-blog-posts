# React for Beginners

v1
v2
v3
v4
v5
v6

v7: props are how you supply data from one component to another

v8: Stateless Functional Component - for when you are just rendering HTML to the DOM.  It doesn't make sense to use
an entire React component.

v9: using React Router 4; basically industry standard. Show and hide

-----

v13 - covers state
React stores all your data in one master object called "state"

you edit the data, React will edit the HTML for you

-----

### Updating Order State - lesson 16

1. Create a variables in Fish.js

```javascript
const isAvailable = details.status === 'available';`
`const buttonText = isAvailable ? 'Add To Order' ? 'Sold Out!';
```

2. replace the static button text with our new variable:
```html
<button>{buttonText}</button>
```

3. Disable the button when unavailable:
```html
<button disabled={!isAvailable}>{buttonText}</button>
```

4. Create a method to add the order to the order column on our page

  open `app.js`

-----

### Persisting state with Firebase - lesson 18

[Firebase](firebase.com) from Google
  * uses web sockets
  * Realtime backend database
    * multiple people can edit at once
    * data is always synced to everyones computer
  * Think of your data as one big
    * works well with React because state is one big object

-----

1. Open the database rules for development (THIS NEEDS TO BE SECURED LATER)

>warningYour security rules are defined as public, anyone can read or write to your database

```javascript
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
2. Sync the fishes{} state with firebase using rebase

  create `src/base.js`:

```javascript
import Rebase from "re-base";

const base = Rebase.createClass({
  apiKey: "AIzaSyBrOBOlyLPY8MeaHXLHTvDv-rhU-Dxys0M",
  authDomain: "catch-of-the-day-jva.firebaseapp.com",
  databaseURL: "https://catch-of-the-day-jva.firebaseio.com"
});

export default base;
```

apiKey, authDomain, databaseURL come from the "Add firebase to your web app " page. It is ok to put the API key on the client side because of firebase's authentication rules (these still need to be setup)

`import base from "../base";`




-----
