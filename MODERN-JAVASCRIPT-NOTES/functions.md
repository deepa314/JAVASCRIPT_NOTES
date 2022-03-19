# Callback Functions

A `Callback functions` is function that is performed after another function has completed its execution. <br>
* It is typically supplied as an input to other function.
* __Callbacks__ are critical to understand, as they are used in array methods (such as __map()__, __filter()__, and so on), __setTimeout__, __eventlisteners__ (such as __click__, __scroll__). <br>

E.g.

```JavaScript
function orderPizza(type, name, callback) {
    console.log('Pizza ordered');
    console.log('Pizza is on preparation');

    setTimeout(function() {
        let msg = `Your ${type} ${name} Pizza is ready`;
        callback(msg);
    }, 3000);
}
```

Now Invocation of orderPizza:

```JavaScript
orderPizza('veg', 'cheese', function (message) {
    console.log(message);
});
```

__Important points to Note:__

* JavaScript function can accept other function as arguement.
* passing function as arguement is powerful programming concept that can be used to notify caller that something happened. <br> It is also known as __callback function__.
* Nesting too many callback function is not a great idea and it creates callback hell.

## JavaScript Map

The __Array.map()__ allows you to iterate over array using loop.

* This method allows you to __iterate__ and __modify__ its elements using a callback function.
* The callback function will then be executed on __each of array's element.__ <br>

__For example:__ <br>
Now Imagine you have to multiply each element of array by 3.<br>
You can use __for loop__ also like this,

```JavaScript
let arr = [2, 3, 4, 5, 6];
for (let i = 0; i < arr.length; i++) {
    arr[i] = arr[i] * 3;
}
console.log(arr); // [ 6, 9, 12, 15, 18 ]
```

By using __map__ it will look like this, 

```JavaScript
let arr = [2, 3, 4, 5, 6]; 
let modifiedArr = arr.map(function(el){
    return el * 3;
});
console.log(modifiedArr); // [ 6, 9, 12, 15, 18 ]
```

## How to use Map over Array of Object

```JavaScript
let users = [
    { firstName: 'Deepa', lastName: 'Chaurasia' }, 
    { firstName: 'Devesh', lastName: 'Chaurasia' }, 
    { firstName: 'Crescent', lastName: 'Partha' }
];

// you can iterate as follow
let userFullNames = users.map(function(el){
    return `${el.firstName} ${el.lastName}`;
});

console.log(userFullNames);
// ['Deepa Chaurasia', 'Devesh Chaurasia', 'Crescent Partha']
```

## The complete map() method syntax

The syntax of __map()__ as follows: <br>
`arr.map(function(element, index, array{}, this);` <br>

* The __Callback function()__ is called on each array element, and the map() method always passes the current element, the index of current element and whole array object to it.
* The __this__ arguement will be used inside __Callback function__.
* By default it's value is __undefined__. <br>

E.g.

```JavaScript
let arr = [2, 3, 5, 7];
arr.map(function(element, index, array){
    console.log(this) // 80
}, 80);
```
Here, you can see this value is __80__ which is __default__ value.

## Reduce Method in JavaScript

__Use it When:__ You have array of numbers, you want to add them all. <br>
E.g.

```JavaScript
const num = [23, 29, 40, 30];
const sum = num.reduce((total, amount) => total + amount);
console.log(sum) // 122
```

## filter() and find() in JavaScript

`filter()` provides new array depending on certain criteria. <br>

Unlike __map()__, it can alter size of new array, whereas __find()__ return just a single instance. <br>

E.g.

```JavaScript
let users = [
    { firstName: 'Ram', age: 15 },
    { firstName: 'Shyam', age: 17 },
    { firstName: 'Jodu', age: 25 }
];
```
You could choose to __sort__ these data by age groups, such as young (1-15) adult (15-50). <br>

Like this, 

```JavaScript
const youngPeople = users.filter((person) => {
    return person.age <= 15; 
});
const adult = users.filter((person) => {
    return person.age >= 50;
});

console.log(youngPeople); // [{firstName: 'Ram', age: 15}]
console.log(adult); // []
```

And the example of __find__ goes like this, 

```JavaScript
const ram = users.find((person) => person.firstName === 'ram');
console.log(ram); // undefined
```

## Unique Value - set() in JavaScript

```JavaScript
let animals = [
    { name: 'Lion', category: 'wild' }, 
    { name: 'Dog', category: 'pet' }, 
    { name: 'Cat', category: 'pet' }
];
```

If we loop through __map__, we will get repeated value. <br>
But we don't want repeated value here, So we will use Unique value - __set()__ <br>
E.g.

```JavaScript
let category = [...new Set(animals.map((animal) => animal.category))];
console.log(category); // [wild, pet]
```


