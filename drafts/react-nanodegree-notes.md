# React Nano-degree

Slack Office Hours
The React Slack channel is also important because one or more members of the Udacity team will hold Office Hours here. During office hours, we'll answer any and all questions you have, whether it's about the content, projects, services, or anything else related to React. These are generally held on Tuesday from 3pm-4pm PST, and on Friday from 10am-11am PST.
33
we've created an issue-reporting board.

——-

## Section 2

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
