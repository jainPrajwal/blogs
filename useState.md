# useState

useState is a react API to change the state of elements or components.
Why do we require a seperate hook to change a value of an element?<br>
Well,Its always a bad practise to mutate the state directly.<br>
Let me explain things along with the code itself.

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

What does this code aim to do?<br>
We want to display user's name instead of just user as a text when button is clicked.<br>
A bad dev like me would probably do something as <p style="color:red">(which is wrong)</p>

```JSX
import "./styles.css";
export default function App() {
  let user = "user";
  return (
    <div className="App">
      <h1>sample program to show declarative programming</h1>
      <hr />
      <button
        onClick={() => {
          user = "prajwal";
          console.log("from onclick", user);
        }}
      >
        Click Me{" "}
      </button>
      {console.log(user, "this is from user")}
      <h1>welcome {user}</h1>
    </div>
  );
}
```

<br>

> _Note: I am purposely showing the wrong approach.Sometimes looking at what is wrong helps us understanding what is correct!!_

<br>

Here goes the sandbox link for the right approach.

{% codesandbox bqw1u  %}

If you see the console.log within onClick you could see that the value of user has been updated.But Wait!Why isnt it reflecting in the view?

Its because..

1. if there is no setState =>(implies) React does not see any state changed => re-rendering of function does not occur => view would no be updated.

2. if you dont use setState, `{console.log(user, "this is from user")}` does not run => function is not called => rerendering does not occur.

Conclusion:<br> <b>only when the state is changed through setState the re-rendering of function occurs.</b>

Thank you for reading till the end. If you notice something wrong do suggest me in the comment box.
Do give it a like if it helped you understanding the concept.
