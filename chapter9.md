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


