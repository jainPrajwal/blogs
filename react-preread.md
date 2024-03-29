# what is declarative in terms of react?

if you are new to react then you might have heard about react being declarative.
What exacly does that mean?Lets have a look.

Say we have a button with us and initially a normal text of welcome user.

**What we want to do?**

We want to display user's name instead of just user as a text when button is clicked.

Lets have a look at the following code.

```html
<h1>sample for showing that react is declarative</h1>
<hr />
<button id="btn-click">Click me</button>
<div>
  <h2>welcome <span id="user">user</span></h2>
</div>
```

Here is what we do in vanilla javascript.

```javascript
document.querySelector("#btn-click").addEventListener("click", () => {
  document.querySelector("#user").innerText = "prajwal";
});
```

{% codepen https://codepen.io/prajwal_/pen/NWpbvBV %}
So we need to tell the browser each and every step which are as follows:

1. hey browser, give me the button which lies on the document whose id is ....(btn-click) in our case.
2. Do something (step 3) when user clicks on that button.
3. when user clicks on that button,give me that element which lies on the document and whose id is ....(user in our case)
4. set the text as ....(prajwal in our case) on it.

Some crucial points to be noted:

1. we are dealing with the browser's DOM to perform our actions.This,is what we dont do in React.We never interact with DOM in React.
   So after the birth of react this procedure seems more like a donkey work.
2. We are telling browser each and every instruction and then it does something for us.

Here is the codepen link if you wish to try your hands on

React has came out with a smarter approach and thats nothing but declarative!

Lets see the react code..

```JSX
import { useState } from "react";
import "./styles.css";
export default function App() {
  let [user, setUser] = useState("user");
  return (
    <div className="App">
      <h1>sample program to show declarative programming</h1>
      <hr />
      <button
        onClick={() => {
          user = "prajwal";
          setUser(user);
          // if you dont use setState line no 19 does not run => function is not called => rerendering does not occur.
          console.log("from onclick", user);
        }}
      >
        Click Me{" "}
      </button>
      {console.log(user)}
      <h1>welcome {user}</h1>
    </div>
  );
}
```

Here is the code for you to play with.

{% codesandbox bqw1u  %}

Again if you dont know about useState you can read [this](https://dev.to/j836/why-use-usestate-1cd9 "useState blog") blog.I have tried to explain things in a simpler way with the same example so that it is relatable.I do suggest you to check out [this](https://dev.to/j836/why-use-usestate-1cd9 "useState blog") blog.

In this react code,you see we only tell the react..<br> Hey React,I want to display something... on this element when some one clicks on the button.
Neither we do document.querySelector nor we do .innerText..i.e. We dont deal direclty with browser's DOM.But still the work is done.How?Well,React does all of that for us.

you see,We dont give set of long instructions.
We only tell react what to do..how does react do that is react's look out.<br>
Its more like saying

## TL;DR <br>

<em>"suun react,tuze ye element pe ye text dikhana hai..kuch bhi kar kaise bhi kar bass kaam ho jaana chaiye..!"<br></em>
Thats declarative!

<!--  So here is all the proof thaat shows react is declarative! Here you need to tell the browser eaach and every step as follows
1. give me the button which lies on the document whose id is ....
2.Do something when user clicks on that button
3.give me that element which lies on the document and whose id is user.
 4.set the text as .... on it.


-->

<!--  In react
Hey React,I want to display ... on this element when some one clicks on the button.
this is declarative
-->
