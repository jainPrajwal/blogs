# Behind the Scenes of React

Arent you guys curious🤔 about what does React do behind the scenes and how it does so many things for us..?

Well,this blog comes out of my curiosity of how the developers at facebook came to create this wonderful thing which caused a revoltion in the World of Web.

Do you know that react has its own DOM!Ya,you got it!same as that of browser has!

Okay.You may think thats great!But why would someone need an Extra DOM?
Eventually,whatever changes are going to occur are on the brwoser's DOM, right?

Well,thats true..But but but...there are some crucial points we need to understand.



2.Whenever a component's state changes,code is re rendered by DOM, and browser has to repaint each and every element on the screen.This involves a lot of mathematical and other calculations.
So our browser is doing unnecessary cycling of complete DOM whereas only a single elements' state has changed.Thus,More the items to repaint slower the app.

And that's the reason why,React has Virtual DOM.
It helps in minimizing the actual changes on browser DOM.How?

Lets see.

Initally,virtual DOM will be an exact copy of real DOM.

In React,whenever a components' state changes,the changes are reflected in Virtual DOM.
Thus,Virtual DOM has the updated state of the component.

Now it checks

```javascript
if(VirtualDOM === Browsers DOM) {
    just chill man!
}
else {
    update the browsers DOM only where that component has changed.
}
```

This is a high level overview of what diffing algorithm does.

Thus,browsers' work has highly reduced and now it will help us loading our app faster!

The process through which React updates the DOM is known as Reconciliation.
This reconciliation has 2 phases :
Render Phase
Commit Phase

## Render Phase

The Render phase takes your JSX and turns it into a javascript representation. This is nothing but the VirtualDOM.

## Commit Phase

The commit phase is actually taking that representation and applying it to the real DOM.
The commit phase is where React actually touches the DOM and makes changes.

An Importatnt Point:
React does not commit state changes one after the other if there are multiple state changes.
Instead,
React goes through its virtual DOM ,creates a list of those changes that need to be made to the actual DOM and then does it all in one single process.
In fancy words,React does batch updates.

So putting all pieces together,
Reconciliation = Render + Diffing occurs in between + Commit.

If there is no change in the state then commit is not done although render has occured.

Now that you have understood reconcilitaion lets understand how diffing works and different factors that affect diffing.

React works on heursitic search.In simple terms,a heuristic search is a technique which has some previous knowledge about the search.
So the assumptions(knowledge) that the React has is:

Two elements of different types will produce different trees.
For a stable re-render key props are required on child elements.(Refer Docs)

Whenever the root elements have different types,
for eg. initialliy it was

```html
<h1>Hello React</h1>
```

and then we change it to

```html
<p>Hello React</p>
```

React will destroy the old tree and build the new tree from scratch. All the children will also get destroyed.
Destroying old tree => all the state associated with it is gone.

## DOM Elements Of The Same Type

When comparing two React DOM elements of the same type,react only updates the changed attributes.
Same goes when updating style.
For eg:

```html
<h1 className="hero">Hello React</h1>
```

is changed to

```html
<h1 className="header">Hello React</h1>
```

When only the attributes are changed,DOM nodes are not recreated => state is maintained =>component is already on the page => DOM does not need to repaint the DOM styles on the view.This is what makes React super fast!

## Component Elements Of The Same Type

> Now we are on COMPONENTS of same type.Earlier it was DOM elements of same type.

Instead of reiterating what docs has written,read react docs.It has been beautifully explained there along with simple examples.

Thats it from this blog!
If you found this post useful do react to this post, which inspires me to write more. If you have any comments or corrections that could improve this post, I would be glad to receive them. Thank you for your time 👋🏼 💙.
