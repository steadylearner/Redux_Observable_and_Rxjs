# Redux_Observable_and_Rxjs

* [timer, takeuntil, takelast, take] 
* [delay, retry, catchError]
* [debounce <-> throttle, distintUntilChanged, switch(Map)] 
* [combineLaetst(combine streams(observable) from two distint elements, similar to zip ]
* [finally, subsrcibe, unsubscribe]

## RXJS link(Some are deprecated, but still useful, compare them with official api)

 * https://rxjs-dev.firebaseapp.com/api/index/from
 * https://www.learnrxjs.io/
 * https://angularfirebase.com/lessons/rxjs-quickstart-with-20-examples/#Excellent-Resources
 * http://rxmarbles.com/
 * https://www.sitepoint.com/rxjs-functions-with-examples/
 
## Redux Observable
(Learn rxjs first, Configuration and use with existing code base is not easy, side effects affect functional programming?)

 * https://redux-observable.js.org/docs/ -> official site(Need to have more examples)
 
 ### Blog Posts
 
 * https://medium.com/@benlesh/redux-observable-ec0b00d2eb52
 * https://medium.com/dailyjs/using-redux-observable-to-handle-asynchronous-logic-in-redux-d49194742522
 * https://medium.com/@mutebg/learn-rxjs-by-examples-c56bf481bec2
 * https://medium.com/@mohandere/rxjs-5-in-5-minutes-1c3b4ed0d8cc

 ### Video Courses
 

 
 ### Practice
 
 * https://medium.com/@mutebg/learn-rxjs-by-examples-c56bf481bec2
 
### Object

 1. delay for specific time and cancel when data fetch end(timer + takeuntil), cancel next element with autoplay(takeuntil)
 2. optimization of async search(debounce, distinUntilChanged, switchMap, takeuntil, delay, retry, takeUntil, catchError)
 
### Next 

 1. Learn graphql and backend and Use it with rxjs and redux
 2. Refactor app and make not found message at first render and refresh, delay showing loading component  
