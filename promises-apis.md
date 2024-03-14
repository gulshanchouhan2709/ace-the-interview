# Promise APIs (all, allSettled, race, any)

###

Promise APIs which are majorly used:
- Promise.all()
- Promise.allSettled()
- Promise.race()
- Promise.any()

### Promise.all()
> Promise.all() like a manager who wants to make sure all employees finish their tasks before they leave work.

Imagine you have three employees doing different tasks, and each one takes a different amount of time to complete their task. You want to ensure that all tasks are finished before you close the office for the day.

So, you tell all three employees to start their tasks, and you wait until they all come back to you saying, "I'm done!"

That's exactly what Promise.all() does in JavaScript:

- You give it an array of promises, each representing a task.
- It waits until all those promises are resolved (or finished).
- Once all the promises are resolved, Promise.all() resolves with an array containing the resolved values of each promise.
- If any of the promises in the array rejects (i.e., one of the tasks fails), Promise.all() immediately rejects with the reason of the first rejected promise.

=====================

Promise.all([p1, p2, p3]) -> Lets assume we are making 3 API call to fetch data. Also assume **p1** takes **3 seconds**, **p2** takes **1 second**, **p3** takes **2 seconds**.  

In first scenario let's assume all 3 promises are successful. So Promise.all will take **3secs** and will give promise value of result like [val1, val2, val3]. It will wait for all of them to finish then it will collect the results and give array as output.  


### Promise.allSettled()

Promise.allSettled() like a reporter who wants to gather information about what happened with every task, whether they succeeded or failed.

Imagine you have three tasks assigned to different workers, and you want to know the outcome of each task. Some tasks might succeed, while others might fail.

So, you ask each worker to finish their task, and once they're all done, you collect the information about whether each task succeeded or failed, and what the result or reason was.

That's what Promise.allSettled() does:

- It waits for all tasks to be completed, regardless of whether they succeed or fail.
- Once all tasks are done, it gives you a report detailing the outcome of each task, including whether it succeeded or failed, and if it failed, why it failed.

💡 Promise.all() -> Fail Fast  
💡 Promise.allSettled() -> Will wait and provide accumulative result

### Promise.race()

Promise.race() like a race among promises.

Imagine you have multiple runners (promises) lined up for a race. The first runner to reach the finish line wins the race, and the race ends immediately, even if other runners are still running.

That's what Promise.race() does:

- You give it an array of promises, each representing a task.
- It waits for the first promise to settle, whether it resolves (finishes successfully) or rejects (fails).
- Once the first promise settles, Promise.race() immediately resolves or rejects with the outcome of that promise, and the race ends.


### Promise.any()

Promise.any() like a hopeful gambler at a casino.

Imagine you have several slot machines (promises) to try your luck on. You put your money into each slot machine and hope that at least one of them will give you a prize. You don't care which slot machine it is, as long as one of them gives you a win.

That's what Promise.any() does:

- You give it an array of promises, each representing a chance to win a prize.
- It waits for the first promise to resolve (finish successfully).
- Once the first promise resolves, Promise.any() immediately resolves with the value of that promise.
- If all promises reject (fail), Promise.any() rejects with an AggregateError containing all rejection reasons.

## Code Examples:

### Promise.all()

```js
// 📌 First Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 1000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P3 Success');
  }, 2000);
});

Promise.all([p1, p2, p3]).then((results) => {
  console.log(results); // ['P1 Success', 'P2 Success', 'P3 Success'] -> took 3 secs
});
```

```js
// 📌 Second Scenario


const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P2 Fail');
  }, 1000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P3 Success');
  }, 2000);
});

Promise.all([p1, p2, p3])
  .then(results => console.log(results))
  .catch(err => console.error(err)); // throws error after 1 sec i.e. 'P2 Fails'
```

### Promise.allSettled()

💡This is safest among all Promises API.

```js
const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 1000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.allSettled([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => console.error(err));

// Over here, it will wait for all promises to be either settled or rejected and then return,
  /*
    [
      {status: 'fulfilled', value: 'P1 Success'},
      {status: 'fulfilled', value: 'P2 Success'},
      {status: 'rejected', reason: 'P3 Fail'}
    ]
  */
```

### Promise.race()

```js
// 📌 First Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 1000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.race([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => console.error(err));

 // It will return as soon as first promise is resolved or rejected.
 // In above example O/P: "P2 Success"
```

```js
// 📌 Second Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 5000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.race([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => console.error(err));

 //After 2 secs O/P: "P3 Fail"
```

Notes:  
* Once promise is settled, it means -> got the result. Moreover, settled is broadly divided into two categories:
1. resolve, success, fulfilled
2. reject, failure, rejected

### Promise.any()

```js
// 📌 First Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P1 Success');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 5000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.any([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => console.error(err));

// It will wait for first settled **success**
// In above, p3 will settled first, but since it is rejected, so it will wait further so at 3rd second it will print "P1 Success"
```

```js
// 📌 Second Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P1 Fail');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('P2 Success');
  }, 5000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.any([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => console.error(err));

// After 5 secs: 'P2 Success'
```

```js
// 📌 Third Scenario

const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P1 Fail');
  }, 3000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P2 Fail');
  }, 5000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject('P3 Fail');
  }, 2000);
});

Promise.any([p1, p2, p3])
  .then((results) => console.log(results))
  .catch(err => {
    console.error(err);
    console.error(err.errors); // ['P1 Fail', 'P2 Fail', 'P3 Fail']
  });

// Since all are rejected, so it will give "aggregate error" as output
// AggregateError: All promises were rejected
// To get AggregateError array you need to write "err.errors"
```

### Summary
There are 6 static methods of Promise class:

> Promise.all(promises) – waits for all promises to resolve and returns an array of their results. If any of the given promises rejects, it becomes the error of Promise.all, and all other results are ignored.

> Promise.allSettled(promises) (recently added method) – waits for all promises to settle and returns their results as an array of objects with:
status: "fulfilled" or "rejected"
value (if fulfilled) or reason (if rejected).

> Promise.race(promises) – waits for the first promise to settle, and its result/error becomes the outcome.

> Promise.any(promises) (recently added method) – waits for the first promise to fulfill, and its result becomes the outcome. If all of the given promises are rejected, AggregateError becomes the error of Promise.any.

> Promise.resolve(value) – makes a resolved promise with the given value.

> Promise.reject(error) – makes a rejected promise with the given error.
Of all these, Promise.all is probably the most common in practice.


<hr>
