# Promises in JavaScript

A `promises` is a javascript object that allows you to make asynchronous calls. <br>
It produces a value when async operation completes successfully or produces an error if it doesn't complete. <br>

You can create __promise__ using __constructor__:

```JavaScript
let promise = new Promise (function(resolve, reject){

})
```

__Executor function takes two arguements:-__
* `resolve` - indicate successful completion 
* `reject` - indicates an error

## The Promise Objects and States

The __Promise Object__ should be capable of informing consumers when execution has been started, completed in returned with an error.

1. __State__ 
   * `pending` - when execution function starts
   * `fulfilled` - when promise resolved successfully
   * `rejected` - when the promise rejects
2. __result__ 
   * `undefined` - initially when state value is pending
   * `value` - when promise is resolved
   * `error` - when the promise is rejected

A __promise__ that is either resolved or rejected are settled.

## Handling Promises by Consumer

__Three important handler methods:__ 
* `then()`
* `catch()`
* `finally()`

These methods helps us create a link between executor and consumer.

## The .then() Promise Handler

It is used to let consumer know outcome of promise. It accept two arguements:
* __result__
* __error__ <br>

E.g.

```JavaScript
promise.then(
    (result) => {
        console.log(result);
    },
    (error) => {
        console.log(error);
    }
);
```

## The .catch() Promise Handler

To handle error(rejections) from Promises. 
It's better syntax to handle error than handling it with __.then()__ <br>

E.g.

```JavaScript
promise.catch(function(error){
    console.log(error);
});
```

## The .finally() Promise Handler

The __funally()__ handler method performs cleanups like stopping a loader, closing a live connection and so on. <br>
Irrespective of whether promise resolve or rejects, the __finally()__ method will run. <br>

E.g.

```JavaScript
promise.finally( () => {
    console.log('Promise Settled');
}).then((result) => {
    console.log({result});
});
```

__Important point to note,__

The __finally()__ method passes through result or error to the next handler which can call a __.then()__ or __.catch()__ again.



