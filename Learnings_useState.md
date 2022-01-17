## the wrong way

```jsx
let [isModeDark, setModeToDark] = useState(false);
let [modeText, setModeText] = useState("dark");
let [isParaHidden, setHidePara] = useState(false);
let [hideText, setHideText] = useState("Hide");
```

```jsx
<button>Switch to {modeText} mode </button>
```

```jsx
<button>{hideText} Para </button>
```

# Learning : Never ever ever use state for something which in turn again depends on some other state.

For eg here hideText and ModeText completely depends on isParaHidden and isModeDark states respectively.

And there is no need of using state for these variables.They can simply be normal variables which change their values according to the state.
For eg for the above modeText and hideText variables,instead of having them in state, we can simply have something as

## the right way

<br>

```javascript
let modeText = "dark";
if (isModeDark) {
  modeText = "light";
} else {
  modeText = "dark";
}
```

and

```javascript
let hideText = "hide";
if (isParaHidden) {
  hideText = "Show";
} else {
  hideText = "Hide";
}
```

As a beginner in React,I found this an useful learning.
Do tell me in the comment box below if you like such small #learning blogs.
I am eager to know what you think about it!

## Objects and Arrays

let [myObj, setObj] = useState({
aaloo: 1
});

## Wrong Way

```javascript
<button
  onClick={() => {
    setObj(++myObj.aaloo);
    // this overwrites the value of myObj itself!So this is wrong
  }}
>
  Increment aaloo
</button>
```

```javascript
<button
  onClick={() => {
    myObj.aaloo++;
    setObj(myObj);

>
  Increment aaloo
</button>
```

here the problem is the function is not re-rendered.Why?
Because the reference og myObj is same!!
Internal properties of obj has changed but obj ka reference is still the same.
Thus React observes no changes and does not re-render the function.
So Everytime we setState of an Array or Object we return new Array or Object.
}}

```javascript
let [myObj, setObj] = useState({
    aaloo: 1,
    tomato: 33,
    bhujia: 45,
    paneer: 22
  });
 <button
        onClick={() => {


          setObj({ ...myObj, aaloo: ++myObj.aaloo });
          // Thus all the values re retained now
          console.log("after inc aalo", { myObj });
        }}
      >
```

`setObj({ aaloo: ++myObj.aaloo });`
By doing this , we update aalo;'s value and return new Onbject..
But this new object lost the properties which we actually has..tomato,paneer bhujia ,etc.
And thus we use destructuring!!!!

## FILL ITIME SHEET
