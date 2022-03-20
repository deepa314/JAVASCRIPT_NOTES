# Synchronous Vs Asynchronous

__`Synchronous:`__ Every statement of code get executed one by one.<br>
So basically, a statement has to wait for earlier statement of get executed.<br>
E.g.

```JavaScript
console.log('I');
console.log('eat');
console.log('ice-cream');
```

> It will print `I` first, then `eat`, after that `ice-cream`

__`Asynchronous:`__ It allows program to be executed immediately without blocking the code. Unlike the Synchronous method it doesn't wait for earlier statement to get executed first. <br>
Each task execute completed independently.<br>
E.g.<br>

```JavaScript
console.log('I');
setTimeout( () => {
    console.log('eat');
}, 2000);
console.log("Ice Cream");
```

It will print

```Output
"I"
"Ice Cream" (will execute immediately)
"eat" (will print after 2 seconds later)
```

## Asynchronous Functions

It contains `async` keyword.
How to use in Normal Function declaration

```JavaScript
async function name (arg) {

}
```

How to use in an `arrow function`

```JavaScript
const functionName = async (arg) => {

}
```

## Asynchronous functions always return promises

It doesn't matter what you return. The returned value will always be `promise`.<br>
E.g.

```JavaScript
const getOne = async => {
    return 1;
}
const promise = getOne();
console.log(promise); // 1
```

### **The await Keyword**

The `await` keyword lets you wait for promise to resolve. Once promise is resolved, it returns the parameter passed into then call. <br>
E.g.

```JavaScript
const getOne = async () => {
    return 1;
}
getOne().then( value => {
    console.log(value); // 1
});
```

Now use of `await` keyword

```JavaScript
const test = async () => {
    const one = await getOne();
    console.log(one);
}
test();
```

We can only use `await` when we have `async`.

### Let's implement the `Fetch API` code using `async/await`:

```JavaScript
const fetchData = async () => {
    const qoutes = await fetch('https://jsonplaceholder.typicode.com/comments');
    const response = await qoutes.json();
    console.log(response);
}
fetchData();
```

We can also handle errors in async/await by using `try` and `catch`.

```JavaScript
const fetchData = async () => {
    try {
        const quotes = await fetch('https://jsonplaceholder.typicode.com/todos/1');
        const response = await quotes.json();
        console.log(respose);
    }
    catch (error) {
        console.log(error);
    }
};
fetchData();
```

