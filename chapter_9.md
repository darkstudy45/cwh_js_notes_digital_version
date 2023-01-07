

# Chapter 9 - Call backs, promises & async/await

Asynchronous actions are the actions that we initiate and they finish later. eg. set Timeout now Synchronous actions" "finish one- by-one

## callback function

are the actions that initiate and A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to Complete an an action. Here is an example of a callback:

```javascript
function loadscirpt(src, callback){
    var scirpt = document.createElement('script');
    scirpt.src=src;


    scirpt.onload=callback()
    document.body.appendChild(scirpt);
}
```

Now we can do something like this:

```js
load Script('https://cdn. harry.com', (script) => {
    afert('Script is loaded")
alert(scrupt src)
});
```

This is called " callback- based" style of async programming. A function that asynchronously should provide a callback we put the function to run where Complete

Handling errors does something Callback argument after its We can handle callback errors by supplying argument like this:

```js
function load Script (Src, callback) {
......
    script Onload = () => Callback (null, script);
    script onerror= () => callback (new Error ('failed'));
......
......
}
```

Then inside of load Script call: 

```js
loadScript ('cdn/harry', function (error, script) {
    0
    if (error) {
     handle error
    else {
     script loaded
    }
    });
```

## Pyramid of dom

when we have callback inside callbacks, the code gets difficult to manage 

this is called pyramid of dom 

```js
loadscirpt((.....){
  loadscirpt ...
     loadscirpt ... 
        loadscirpt ....

})
```

As calls become more nested the Code becomes  deeper and increasingly more difficult to manage,  especially if we have real rode instead of a..  

This is something called **"callback hell " or "pyramid of dom"**

The "pyramid" of these calls grows to wards the  right with every asynchronous action. Soon it,  Spirals out of control. So this way of coding  isn't very good!

## Introduction to Promises

The  
solution to the callback hell is promises. A promise is a  

> "promise of code excution"

The code either executes or fails in both cases the subscriber will be notified.

The syntax of a promise looks like this 

```js
let promise = new promise(function(resolve,reject{
    // the resolve and reject are predefined in js engine 
    //exucutor 
})
```

resolve and reject are two callbacks provided by javascirpt itself . They are called like this: 

```js
resolve(value)---> if the job is finished sucessfully
reject(error)----> if the job fails 
```

The promise object returned by the new promise constructor has the properties.

1. state: Initially pending then changes to either "fulfilled" when resolve is called or "rejected " when reject is called . 

2. result: Initially undefined , then cahnges to value if resolved(value) or erro when rejected(error)

## Consumer: then & catch

The consuming code can recieve the final result of a promise through then and catch 

The most fundamental one is then 

```js
promise.then(function(result){
    /* handle */
},funtion(error){
    // handle 
});
```

If we are interested only in successful completions,  can provide only one function argument to  .then():

```js
let promise = new promise(resolve=>{
    setTimeout(c)=>{
    resolve("done")
    },1000)    
}
```

If we are interested only in errors, we can  use  null as  the first argument: .then (null, f) or  can use catch:"

```js
promise.catch(alert)

promise.finally(c)=>({})// is used to perform general cleanups
```



**Quick quiz:** Rewrite the load Script function  in the beginning of this chapter using  
promises

## promise chaining

we can chain promises and make them pass the resolved values to one another like this

```js
p.then(function(result){
    alert(result);
    return 2; 
}).then......
```




