# Object and It's Methods in JavaScript

## How to create object in JavaScript?

```JavaScript
// simple and most popular way to create object
const person = {
    name: 'Deepa'
};
```
You can also use __new__ keyword

```JavaScript
const person1 = new Object();
person1.name = 'Deepa';
console.log(person1); // {name: 'Deepa'}
```

You can also use __'new'__ with user defined constructor function. <br>
E.g.

```JavaScript
function person(name) {
    this.name = name;
}
// Now anytime you want person object.
const personOne = new person('deepa');
const personTwo = new person('partha');
console.log(personOne); // {name: 'deepa'}
console.log(personTwo); // {name: 'partha'}
```

## Using Object.create() to create new Objects

The __Object.create()__ methods creates a new object, using an existing object as prototype of the newly created object. <br>

It contains __two__ parameter:
* First parameter is mandatory that serves prototype of new object to be created.
* Second is optional, it contains properties to be added to new object. <br>

E.g.

```JavaScript
const orgObject = { company: 'ABC' };
const employee = Object.create(orgObject, { name: { value: 'EmpOne'}});
console.log(employee); // {name: 'EmpOne'}
console.log(employee.name); // EmpOne
```

## Using Object.assign() to create new object

The __Obeject.assign()__ method is used to copy all enumerable own properties value from one or more source objects to target object. It will return target object. <br>

E.g.

```JavaScript
const orgObject = { company: 'ABC' };
const carObject = { carName: 'Corola' };
const employee = Object.assign({}, orgObject, carObject);

// Now you can get employee object that has company and carName as its property.

console.log(employee); // {company: 'ABC', carName: 'Corola'}
```

## Using Object.defineProperties()

This method defines __new__ or __modify__ existing property on object.

```JavaScript
const object1 = {};
Object.defineProperties (object1, {
    property1: {
        value: 42
    }
});
console.log(object1.property1); // 42
```
Similarly, we also have __Object.defineProperty()__

## Using Object.Entries()

It returns an array of object's __key value__ pairs. <br>
The order of array is same as provided by a __for__ in loop

```JavaScript
const object1 = {
    a: 'something', 
    b: 'nothing'
};
for (const [key, value] of Object.entries(object1)) {
    console.log(`${key}: ${value}`);
}
/* Output:
    a: something
    b: nothing
*/
```

## Object.freeze()

It freezes an object. No longes can be changed. <br>
E.g.

```JavaScript
const obj = {
    prop: 42
};
Object.freeze(obj);
obj.prop = 43;
console.log(obj.prop); // 42
// It can no longes be change due to freeze
```

## Object.fromEntries()

It transforms a list of __key-value__ pairs into an object. <br>
E.g.

```JavaScript
const entries = new Map([
    [ 'foo', 'bar' ],
    [ 'baz', 42 ]
]);
const obj = Object.fromEntries(entries);
console.log(obj); // {foo: 'bar', baz: 42}
```




