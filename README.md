## Javascript Advance Concept

### Synchronous Programming
> Javascript is bydefault synchronous . JavaScript functions are executed in the sequence they are called. Example:
  
  ```
 const taskOne=()=>{
      console.log("Task One");
  };

  const taskTwo=()=>{
      console.log("Task Two");

  };

  const taskThree=()=>{
      console.log("Task Three done ");
  };

  taskOne();
  taskTwo();
  taskThree();
```
**Output**
```
Task One
Task Two
Task Three done 
```
> As you can see all the functions are  executed in the sequence they are called.But if taskTwo function needs more time to complete it's task in that case function taskThree need to wait,after taskTwo finished it's task then taskThree can executed.So this is a problem of sequence programming which we can resolved by "Asynchronous Concept" 

### Asynchronous
> An asynchronous code allows multiple things to happen at the same time. Example:
```
  const taskOne=()=>{
    console.log("Task One");
};

const dataLoading=()=>{
    console.log("Task-2 data loading");
}

const taskTwo=()=>{
    setTimeout(dataLoading,2000); //callback function
};

const taskThree=()=>{
    console.log("Task Three done before task 2");
};

taskOne();
taskTwo();
taskThree();
```
**Output**
````
Task One
Task Three done before task 2
Task-2 data loading

````
>As you can see, we're calling functions sequentially but function taskThree executed before taskTwo function.The reason is taskTwo function needs more time to complete it's task.Here taskThree will not wait for taskTwo to complete it's task.So taskTwo function will go to queue stack and wait there as we're using setTimeOut() which is working asynchronously,in the meanwhile taskThree will go to call stack and executed first, after that   tasktwo function will go to in callstack and finish it's task. That is Asynchronous concept.

### Javascript callback function
> A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. Example:
```
function greeting=()=> {
  console.log("Hello Everyone!!Ohayo Gozaimasu");
}

function higherOrder(callback) {
  callback();
}

higherOrder(greeting);
```
> Here we're defining a arrow function called greeting,which is passed as an argument in another function called higherOrder and called that greeting function inside that higherOrder function.This is the concept of callback. Another Example collect from  [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)
```
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```
### Promise
> JavaScript is single threaded, meaning that two bits of script cannot run at the same time; they have to run one after another. A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.First of all, a Promise is an object. 
There are 3 states of the Promise object:
- Pending: Initial State, before the Promise succeeds or fails
- Resolved: Completed Promise
- Rejected: Failed Promise
Here is one example:

````
  console.log("Print this console first");

let value1=20;
const promise0bj=new Promise((resolve,reject)=>{
        if(value1%2==0){
            resolve("Number is Even,Fulfilled")
        }
        else{
            reject("Sorry number is not even,Rejected")
        }
    }
);

promise0bj.then((res)=>{  
    console.log(res);
});
console.log("Last console for printing statement");
````
**Output**
````
Print this console first
Last console for printing statement
Number is Even,Fulfilled

````
>As you can see the last console executed before the promiseObj.then() .The reason is Promises are one of the ways to deal with asynchronous operations in javascript.Both first and last console are synchronous so they executed first,then the promise executed.
