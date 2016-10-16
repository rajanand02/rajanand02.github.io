---
layout: post
title: "React ES6 Constructor and super keyword"
category: articles
tags: [React, ES6, Constructor, super, props]
description: "React ES6 Constructor and super keyword"
comments: true
share: true
---

I have seen people getting super confused when comes to ES6  `constructor` and `super` keyword, especially with `React`.

The most common questions are

1. Do we need to a have  a `constructor` in every component ?
2. Do we need to call `super()` inside a constructor?
3. What is the deal with `super()` vs `super(props)` ?

Let's go over the questions one by one.

> Do we need to have a `constructor` in every component? 

The answer is `NO`. if your component is not so complex and it simply returns a node you don't need a constructor at all.

```javascript

class Name extends Component {
    render () {
        return (
            <p> Name: { this.props.name }</p>
        );
    }
}
```

if you have very simple component like the above you don't even need a `class`. It could be simple plain javascript function.

```javascript
function Name(name) {
    return (
        <p> Name: { name } </p>
    );
}
```

if you would like to know why we need a constructor in the first place, I would highly recommend you to head over and read about [ES6 classes](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Classes).

Now comes the second most common question

> Do we need to call `super()` inside a constructor ?

The answer is `YES`. if you would like to set a property or access `this` inside the `constructor` you need to call `super()`.

```javascript
class Name extends Component {
    constructor(props){
        this.firstName = "Jhon"; // 'this' is not allowed before super()
    }
    render () {
        return (
            <p> Name: { this.props.name }</p>
        );
    }
}
```

The above component will throw an error saying `'this' is not allowed before super()`

So now we are clear that we need to call `super()` if we need to use `this` inside the constructor. 

The final and most misunderstood one is

>  What is the deal with `super()` and `super(props)`?

if you need to access the props inside the `constructor` of a `class` then you need to call `super(props)`.

```javascript
class Name extends Component {
    constructor(props){
        super();
        this.state = {
            firstName: this.props.firstName; // here props would be undefined.
        };
    }
    render () {
        return (
            <p> Name: { this.state.firstName }</p>
        );
    }
}
```

it is very common in react to get the `props` from the parent and set it to the local `state` of the component. In that case always call `super()` with the `props`. ie `super(props)`.

If you don't have the `constructor` special method in your class, `React`  will set `this` and `props` for you so that you can access the `props` inside your `render` method as shown in my first example.

```javascript

class Name extends Component {
    render () {
        return (
            <p> Name: { this.props.name }</p>
        );
    }
}
```

##### References
1. [ES6 classes](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Classes)
2. [Airbnb react style guide](https://github.com/airbnb/javascript/tree/master/react#class-vs-reactcreateclass-vs-stateless)
3. [React discussion forum](https://discuss.reactjs.org/t/should-we-include-the-props-parameter-to-class-constructors-when-declaring-components-using-es6-classes/2781)