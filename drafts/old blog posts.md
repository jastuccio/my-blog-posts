Self Hosted Ghost.js Blogging

### linking to your other posts
leave off your site url to link to one of your posts.  The link will work in both locally, `localhost:2368/post_name` and your remote host, `myamazingblog.com/post_name`.
`[link title](/post_name)`

-----

There Should Be A System To Let Readers Update Bugs in Tutorials

While learning to code I have come across several tutorials with bugs in them.  It isn't rational to expect the author to keep the code updated on a free blog post forever.  Reading through all the comments hunting for bugs and fixes doesn't always work either.  

I am imagining something that combines: 
<li>The widespread use of [disqus](https://disqus.com)</li> 
<li>the reputation system of [stackoverflow](http://stackoverflow.com/)</li>
<li>the issue tracking of [github issues](https://github.com/jquery/jquery/issues)</li>

There could be a special 'comment' section near the top before the tutorial startr for unresolved bugs.  That would make it easy to decide if you wanted to go through the tutorial or not.  Users could vote on suggested bug fixes.  If enough users or someone with enough reputation upvoted the code would be changed automatically.  Resolved issues would move somewhere else.  The comments section can get quite long with proposed bug fixes and thank yous.  It is good to say thank you, but reading through comments that contain a bunch of resolved issues can be time consuming and distracting.  This is only the beginning of the idea.

After spending an hour with [codepen](http://codepen.io/), [jshint](jshint.com), [W3C validator](https://jigsaw.w3.org/css-validator/), and writing this post,  I want to get back to finishing that [tutorial](/handlebars-js/).

-----

When you do work that matters, the crowd will call you a fool

Many times when I read [Seth Godin](http://sethgodin.typepad.com/seths_blog/) his posts speak to the core of my being and to the person I want to become.

> If you do something remarkable, something new and something important, not everyone will understand it (at first). Your work is for someone, not everyone.

> Unless you're surrounded only by someones, you will almost certainly encounter everyone. And when you do, they will jeer.

> That's how you'll know you might be onto something.

Posted by Seth Godin on May 24, 2015

TrackBack

TrackBack URL for this entry:
http://www.typepad.com/services/trackback/6a00d83451b31569e201b7c78f6910970b

-----

#####Is it meeting your needs…

Or merely creating new wants?
Is it honoring your time or squandering your time?
Is it connecting you with those you care about, or separating you from them?
Is it exposing you or giving you a place to hide?
Is it important, or only urgent?
Is it right, or simply convenient?
Is it making things better, or merely more pressing?
Is it leveraging your work or wasting it?
What is it for?

Posted by Seth Godin on May 20, 2015

TrackBack URL for this entry:
http://www.typepad.com/services/trackback/6a00d83451b31569e201bb0830bbd4970d

-----

#####Unlimited scale

Nothing grows to infinity. Certainly no project or business or idea.

And saying, "as many as possible," implies a series of trade-offs that you're probably not actually interested in making.

One of the most important decisions we make is almost always made without thought, without discussion:

"How big do you want this to be?"

It's a question that always gets in the way of,

"How good do you want this to be?"

Posted by Seth Godin on May 19, 2015

TrackBack

TrackBack URL for this entry:
http://www.typepad.com/services/trackback/6a00d83451b31569e201b7c6cda601970b

-----

#####Why do you do it this way?

That's the simple test of a bureaucracy that has lost its way.

If your employees can't answer how something they do helps the customer or the company, you've insulated your people from their jobs.

"It's our policy," is not an answer to why. Saying the policy again, louder, is not an answer to why.

Their inability to answer this simple question might be because you haven't taken the time to teach your people how to think about the work you do. Or it might be because you're hiring people (or rewarding people) who don't want to think about your work.

Don't you want the people who do the work to understand it?  And don't you want your customers to feel respected by the people who serve them?

Posted by Seth Godin on May 18, 2015

TrackBack

TrackBack URL for this entry:
http://www.typepad.com/services/trackback/6a00d83451b31569e201b8d114f8d7970c

-----
NodeSchool International Day

Saturday May 23 I attended [NodeSchool in Holyoke, Massachusetts.](https://ti.to/nodeschool-western-massachusetts/nodeschool-international-day-2015)

-----

Learning Meteor in NYC
write about Max Savin's training

-----
Install OSX Applications Using the Terminal

I found a [Github gist](https://gist.github.com/jgarber623/4364590) that installs Google Chrome using the command line.  Why would anyone want to do this?  I am interested in creating an OSX 'setup script' that installs all the applications I use.  The goal is to take a clean install of OS X and get it as close to production ready as possible using a shell script and dot files.

Here is the script:
```shell
curl -Lo /tmp/Google\ Chrome.dmg https://dl.google.com/chrome/mac/stable/GGRO/googlechrome.dmg;
hdiutil attach /tmp/Google\ Chrome.dmg;
ditto -rsrc /Volumes/Google\ Chrome/Google\ Chrome.app /Applications/Google\ Chrome.app;
hdiutil detach /Volumes/Google\ Chrome;
rm /tmp/Google\ Chrome.dmg;
```

I used [explainshell.com](http://explainshell.com/explain?cmd=curl+-Lo+%2Ftmp%2FGoogle%5C+Chrome.dmg+https%3A%2F%2Fdl.google.com%2Fchrome%2Fmac%2Fstable%2FGGRO%2Fgooglechrome.dmg%3B) to help me understand each line.

1st line:
<li>`curl` = [transfer a URL](http://explainshell.com/explain/1/curl)</li>
<li>`L` flag = If the requested page moved curl will redo the
       request on the new place.
<li>`o` flag = Write  output  to `/tmp/Google\ Chrome.dmg` instead of stdout.</li>
<li>`https://dl.google ... googlechrome.dmg` the file path we are downloading.

2nd line:
<li>`hdiutil attach` = attach `/tmp/Google\ Chrome.dmg` as a device.</li>

3rd line:

-----




How George Costanza Would Build Your App

[Remote|ok](https://remoteok.io) is an aggregator that pulls from multiple sites. My favorite way to search through the jobs is by [tags.](https://remoteok.io/tags)
![Remote|Ok job boards](https://levels.io/wp-content/uploads/2015/04/Screenshot-2015-04-02-21.23.11-1024x582.png)

-----

Meteor.js

[Meteor](https://www.meteor.com/) is a complete open source platform for building web and mobile apps in pure JavaScript.  Read the [official documentation.](http://docs.meteor.com/) for additional info.

##File Rules:
  <ul>
    <li>`/lib` Files here load first</li>
    <li>`Main.*` these files load last</li>
    <li>`/server` Code in this directory only runs on the server</li>
    <li>`/client` Code in this directory only runs on the client</li>
    <li>Everything else runs on both</li>
    <li>`/public` Place static assets(fonts, images,etc) here</li>
    <li>`/tests` is not loaded anywhere. Use this for local test code</li>
    <li>`.meteor` Meteor stores its own code in this hidden directory</li>
  </ul>
  
  

##Miscellaneous Commands:
Starting the Meteor server: `$ meteor` and navigate to: `localhost:3000`

Meteor help: `$ meteor help <command_name>`

##Packages

Meteor has 5 basic types of packages:
  <ol>
    <li>core packages - included with every meteor app</li>
  <li>smart packages - come bundled with Meteor</li>
    <ol>
        <li>optionally import them: `meteor add <package name>`</li>
        <li>get the full list: `meteor list`</li>
    </ol>
  <li>local packages - created by you and placed in the `/packages` directory</li>
  <li>Atmosphere packages - third-party Meteor packages listed on [Atmosphere](https://atmospherejs.com/)</li>
  <li>NPM packages - (Node Packaged Modules) are Node.js packages</li>
    <ol>
      <li>don't work out of the box with Meteor</li>
      <li>can be used by the previous types of packages.</li>
    </ol>
</ol>

##Pub/sub

######publication
 inside the `isServer` conditional

```
if (Meteor.isServer) {
    Meteor.publish('arbitraryArgumentName', function(){
        // inside the publish function
    });
}
```

######subscription

==========================================

##Templates
  <ul>
    <li>defined in html files located anywhere in your Meteor project folder EXCEPT the `/server` `/public` or `/private`</li>
    


##make a ‘channels’ collection



1 define collection = create a mongo db in collection.js
`channels = new Mongo.Collection("channels");`
 
2 publish in publication.js 
  4.  subscription
  5.  templates to display it

-----

Extra Dim your iPhone at Night

####How to make your iPhone dimmer than the brightness setting allows without a  jailbreak

I just watched a great video from [Wes Bos](http://wesbos.com/) on making your [iPhone dimmer](mahttps://www.youtube.com/watch?v=ud7cAwmcNB0) than the brightness setting allows. You don't need to jailbreak.  This has been on my wish list for a long time.  I can't wait to try it out tonight.

On your iPhone goto:
<ol>
<li>Settings->General->Accessability->Zoom</li>
<li>turn Zoom on</li>
<li>Set the Zoom Region to full screen</li>
<li>Three finger double tap your iPhone</li>
<li>Choose Filter ->low light</li>
</ol>

####triple clicking home to activate'low light'
<ol>
<li>Settings->General->Accessability->Accessability Shortcut(at the bottom)</li>
<li>choose Zoom</li>
</ol>

Now you can triple click the iPhone to toggle between low light and regular brightness settings!

-----

Virtualbox



List running machines (returns name and UUID):

    VBoxManage list runningvms

Stop running VMs by "hibernating" them (reommended to avoid data loss)

    `VBoxManage controlvm <name|uuid> savestate`

Poweroff running VMs (not recommended because we may lose data in the guest)... VBoxManage controlvm <name|uuid> poweroff

Use ACPI in an ACPI-aware guest OS (preferable to poweroff for graceful shutdown of guests)

    `VBoxManage controlvm <name|uuid> acpipowerbutton`

------

Javascript

parameters vs arguments

hoisting definition

declaration vs expression for both variables and functions

##Strict Mode
* produces more exceptions than warnings
* prohibits the use of some deprecated features

The recommended way to invoke strict mode:

```
(function strictly() {
    "use strict";
    //all your code goes inside this function
} ());
```

[JSLint Error Explanations](http://jslinterrors.com/) is designed to help you improve your JavaScript by understanding the sometimes cryptic error messages produced by JSLint, JSHint and ESLint, and teaching you how to avoid such errors. 

####Feature Detection
* use an if statment to check whether an object or method exists before calling it

####Breakpoints
* halt the code and allow us to view the value of different variables at that point in the program
  * alert()  - *No longer a recommended method of debugging.*
    * stops the program from running until ok is clicked 
  * console.log() - used to log the value of variables at different stages of the program
    * does not stop the execution if the program
  * console.trace() - logs an interactive stack trace in the console
    * shows the called functions leading to an exception
  * console.count() - displays the number of times a line was called
  *console.dir(node) - displays an interactive list of all object properties — like you would normally see in the DOM panel
   *console.dirxml() - displays the node and all descendants — like a section of the HTML panel

   [firefox javascript debugger](https://developer.mozilla.org/en-US/docs/Tools/Debugger) <br>
   [Chrome js debugger](https://developer.chrome.com/devtools/docs/javascript-debugging)
   
####Callbacks
* functions that are passed to other functions as arguments
* facilitate event-driven asynchronous programming(single threaded)

####Closures
*  a reference to a free variable that was created inside the scope of another function

####Classes
  * Javascript does not support classes (ECMAScript will support them)
notes from:
'Javascript Novice to Ninja'

####Mixins
* A way of adding properties and methods of one object to another object without using inheritance

------

Twitter Bootstrap

insert jQuery just inside the <body> tag instead of the <head> tag. This is so that jQuery is loaded after all the HTML contents are loaded, reducing the pageʼs loading time.

##Internet Explorer 8
Bootstrap 3 uses many HTML5 elements and CSS3 properties that wonʼt work 
  *only be called into action for IE8, bringing support for HTML5 and CSS3 in it. These scripts are html5shiv.js and respond.js:
  
  ```
  <!--[if lt IE 9]>
        <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
  <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script> <![endif]-->
  ```

  Did your JavaScript and CSS files load properly?
    *go to Inspect Element
      * Console tab - if no errors are displayed, all the JavaScript files have loaded properly
      *  Network tab - no 404 errors, all the CSS files are linked properly

##Offsetting
  * generally used to increase the left margin of a column
  ```col-xs-offset-*```

## Push & Pull
reorder the columns irrespective of the order in which they're written
```col-xs-pull-*``` and ```col-xs-push-*``` for extra smaller screens

##class="thumbnail"

##class="media"

-----

##FizzBuzz Refactored.  My Solution in 5 Lines.

Originally this was posted on the [Codecademy forum](http://www.codecademy.com/forum_questions/52ae8600631fe92cc000a168/edit) when I was learning javascript.  I was excited that I searched for examples online and was able to understand the code from different examples.  I combined them into my own solution.  After posting I was able to answer some questions about how the code works.  Below is a 

---
Tonight I refactored my code and I really like what I came up with.  I picked up the 'append to' idea in a tutorial somewhere.  One of my professors said that its usually better not to repeat math operations.  This solution only divides by 3 and 5 once each.  My original solution divided by 3, by 5, then by 3 & 5.  

I hope it doesn't come across as bragging.  Ive been studying programming for awhile and feel like it is finally starting to make sense :)  Id like to see a "best solutions" section on the Codecademy forum.  I learned a lot by looking at other peoples code.

```javascript
for (var i = 1; i <= 20; i++) {
    var result = "";
    if (i % 3 === 0)    { result = "Fizz"; }
    if (i % 5 === 0)    { result += "Buzz"; }
    if (result === "")  { result = i; }
    console.log(result);
}
```

 1. start the loop
 2. create a variable to hold Fizz, Buzz, or the number.  It also resets the variable at the start of each loop
 3. change result to Fizz for multiples of 3
 4. APPEND Buzz using += to the result for multiples of 5
 5. If the result is still "" that means it was not divisible by 3 or 5, change result to the variable i ( the number)
 6. console log the result variable

---

####REFACTORED!  Now one line shorter.

```javascript
for (var i = 1; i <= 20; i++) {
    var result = "";
    if (i % 3 === 0)    { result = "Fizz"; }
    if (i % 5 === 0)    { result += "Buzz"; }
    console.log(result || i);
}
```


I deleted line 5.  `if (result === "")  { result = i; }` and added `|| i` to what was line 6.  I saw this used in someone else solution and was going to link to it, but I lost the page.  `console.log(result || i);`

---

Who knew id learn so much from FizzBuzz. There are even [videos](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=tdd+javascript+fizzbuzz&tbm=vid) about TDD (test driven development) and FizzBuzz.  I will be watching them later to see what else I can learn.  

What is exciting is that programming is starting to make sense to me.  I can read other peoples code then improve my code based on what I learned!


A quick search on Google shows im not even close to the [smallest code](http://rosettacode.org/wiki/FizzBuzz#Alternativeversion.28one-liner.29). Oh well....

Alternative version (one-liner):
```javascript
for (var i=1; i<=100; i++) console.log( (i % 3 === 0 ? 'Fizz' : '') + (i % 5 === 0 ? 'Buzz' : '') || i );