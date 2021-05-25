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
