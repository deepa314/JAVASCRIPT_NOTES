# Destructuring

## What is Destructuring in JavaScript?

__Destructuring__ is act of unpacking element in an array of object. <br>
It not only allow you to npack but also manipulate and switch elements according to your demand.

## Destructuring in Arrays

` Rest Operator = ...rest `<br>
E.g.

```JavaScript
const [var1, var2, ...var3] = ['Deepa', 'Jyoti', 'Crescent', 'Partha'];

console.log(var1); // Deepa
console.log(var2); // Jyoti
console.log(var3); // ['Crescent', 'Partha']
```

JavaScript allows you to use `rest operator` with a `destructuring array` to assign the rest of regular array to variable. <br>
As you have noticed __['Crescent', 'Partha']__ remaining both get stored in var3. <br>
E.g.

```JavaScript
const [ , , website ] = [ 'google', 'yahoo', 'firefox' ];
console.log(website); // firefox
```

Here we use ``','`` to skip variables at destructuring array's first and second index positions.

## How Default value work in an Array Destructing Assignment
E.g.

```JavaScript
const [ firstName = 'Deepa', lastName = 'Chaurasia' ] = [ 'Deepa Chaurasia' ];

console.log(firstName); // Deepa Chaurasia
console.log(lastName); // Chaurasia
```

Here **Deepa** and **Chaurasia** are default value of **firstName** and **lastName** variables. <br>
> In our attempt to extract first index value from right side of array, the computes defaulted to **Chaurasia** - because only 0th index value exists in **['Deepa Chaurasia']**

## Object Destructuring in JavaScript

**Object Destructing** is unique technique that allows you to neatly extract an object's value to new variables.

```JavaScript
const profile = {
    firstName: 'Deepa'
};
const { firstName: firstName } = profile;
```
Here, <br>
* `firstName` = This key references the profile object's firstName key
* **firstName** = This value represents yours new variable

> Destructuring object's key references its profile objects property name.

> Destructuring object's value represents your new variable.

E.g.
```JavaScript
const profile = {
    firstName: 'Deepa', 
    lastName: 'Chaurasia'
};
const { firstName, lastName } = profile;

console.log(firstName); // Deepa
console.log(lastName); // Chaurasia
```

## How to Use object Destructuring to Swap Value

```JavaScript
let firstName = 'Crescent';
let lastName = 'Partha';

[{ firstName, lastName } = { firstName: lastName, lastName: firstName }];

console.log(firstName); // Partha
console.log(lastName); // Crescent
```

