# Closures in JavaScript

```JavaScript
function sayWord (word) {
    return () => console.log(word);
}
const sayHello = sayWord('hello');
sayHello(); // hello
```

There's `two` interesting point to notice:

> The returned function from sayWord can `access` the word `parameter`

> The returned function maintain the value of word when sayHello is called `outside scope` of word.

## The first point can be explained by **Lexical Scope**:

__`Lexical Scope:`__ The returned function can access word before it exists in its order scope.

## The second point becouse of **Closures**:

* A `Closure` is a function combined with references to variables define outside of it.
* `Closure` maintain the variable references, which allow function to access variables outside of their scope.
* They `enclose` the function and variable in its environment.

## Example of Closures in JavaScript

**`Callbacks:`**  It is common for a callback to reference a variable declared outside of itself.<br>
E.g. 

```JavaScript
const cars = function getCarsByMake(make) {
    return cars.filter(x => x.make == make);
}
```
make is available in callback becase of lexical scoping and make is persisted when filter called because of closure.

**`Storing State:`** We can use closures from functions that store states.
Let's say a function which returns an object that can store and change name.

```JavaScript
function makePerson(name) {
    let _name = name;
    return {
        setName: (newName) => (_name = newName),
        getName: () => _name
    };
}
const me = makePerson ("deepa");
console.log(me.getName()); // deepa

me.setName("partha");
console.log(me.getName()); // partha
```

It shows how closure don't freeze values of variables from function's outer scope during creation. Instead they maintain the references throughout closure's lifetime.

## Private Methods
So In oops concept, In a class we have private state and expose getter and setter methods public. <br>
We can extend this oops 

```JavaScript
function makePerson(name) {
    let _name = name;
    function privateSetName(newName) {
        _name = newName;
    }
    return {
        setName: (newName) => privateSetName(newName),
        getName: () => _name
    };
}
```

privateSetName is not directly accessible to consumers and it can access the private state variable _name through closure.

## Closures make it possible for:

* functions to maintain connections with outer variables, even outside scope of the variables.
(like LinkedIn maybe:)<br>

* There are many uses of closures from creating class like structures that store state and implement private methods to passing callback to event handless.

