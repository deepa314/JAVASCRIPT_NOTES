# The JavaScript `this` keyword

In JavaScript, __this__ keyword allows us to
* **Reuse functions** in different execution contexts. It means, a function once defined can be invoked for different objects using this keyword.
* **Identifying the object** in the current execution context when we invoke a method.

The **this** keyword is very closely associated with JavaScript functions. <br>
When it comes to this, the fundamental thing to understand where a function is invoked. 
Because we don't know this keyword until the function is invoked.<br>

## Types of Binding in JavaScript

* Default Binding 
* Implicit Binding
* Explicit Binding
* Constructor Call Binding

## Default Binding in JavaScript

One of the first rule to remember is that if the function housing a this reference is **standalone function**, then that function is bound to the **global object**. <br>
For Example:<br>

```JavaScript
// Standalone Function
function alert() {
    console.log(this.name + 'is calling');
}
const name = 'deepa';
alert(); // is calling
```

As you can see, name() is a **standalone**, unattached function, so it is bound to the global scope. <br>
As a result __this.name__ reference resolves to the global variable `const name = 'deepa'`. <br>
This rule doesn't hold if name() were to be defined in strict mode. <br>
It will output `// TypeError: 'this' is undifined` <br>

## Implicit Binding in JavaScript

According to **binding rule** in JavaScript, a function can use  an object as its context only if that object is bound to it at call site. <br>
For Example: <br>

```JavaScript
function alert() {
    console.log(this.age + ' years');
}
const myObj = {
    age: 24, 
    alert: alert
}
myObj.alert() // 24 years
```

When you call a function using **dot notation**, this is implicitly bound to the object the function is being called from. 
In this example Since **alert** is being called from myObj, the this keyword is bound to myObj. <br>
So when alert is called with **myObj.alert()**, then **this.age** is set 22, which is age property of myObj. <br>
Another Example:<br>

```JavaScript
function alert() {
    console.log(this.age + ' years');
}
const myObj = {
    age: 24, 
    alert: alert, 
    nestedObj: {
        age: 26, 
        alert: alert
    }
}
myObj.alert(); // 24 years
myObj.nestedObj.alert(); // 26 years
```

# Explicit binding in JavaScript

If we want to force a function to use an object as its context without putting a property function reference to object. <br>
We have **2 utility methods**:
* **call()**
* **apply()**

Along with other set of utility functions, these 2 utilities are available to all functions in JavaScript via **[[Prototype]]** mechanism. <br>
To explicitly bind a function call to context, you simply invoke a **call()** on that function and pass in context object as parameter. <br>
For Example:<br>

```JavaScript
function alert() {
    console.log(this.age + ' years');
}
const myObj = {
    age: 24
}
alert.call(myObj); // 24 years
```

Even if you were to pass around the function multiple times to new variables, every invocation will use same context because it has been locked (explicitly bound) to that object. <br>
&nbsp;&ensp;&emsp;This is called **hard binding** <br>
For Example:<br>
```JavaScript
function alert() {
    console.log(this.age);
}
const myObj = {
    age: 24
}
const bar = function() {
    alert.call(myObj);
}
bar(); // 24
setTimeout(bar, 100); 24
// a hard bound 'bar' can no longes have it's 'this' context overridden
bar.call(window); // 24
```

**Hard binding** is perfect way to lock a context into a function call and truly make that function into a method. <br>

# Constructor Call Binding in JavaScript

When a function is invoked with **new keyword** in front of it, known as **constructor call**, following things occur.

* A brand new object is created
* The newly constructed object is **[[Prototype]]** - linked to the function that constructed it.
* The newly constructed object is set as the this binding for that function call.

For Example: <br>
```JavaScript
function giveAge(age) {
    this.age = age;
}
const bar = new giveAge(24);
console.log(bar.age); // 24
```

By calling **giveAge(...)** with **new** in front of, we've constructed a new object and set the new objects as the this for call. <br>
So **new** is final way that you can bind a function call's this. <br>

## JavaScript **this** keyword - Explained
Where it's Used:
[`Image_1`](https://www.freecodecamp.org/news/content/images/2021/06/12.png "What does 'this' mean in JavaScript?") | [`Image_2`](https://www.freecodecamp.org/news/content/images/2021/06/13.png "The 'this' keyword explained with examples")

