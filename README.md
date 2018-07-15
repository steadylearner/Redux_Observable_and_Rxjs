# Redux_Observable_and_Rxjs

Just to save what I learn from them.

## Operators

* [tap -> to debug, side effects etc(console, alert etc), doesn't affect event stream]
* [timer, takeuntil, takelast, take] 
* [delay] 
* [retry, catchError]
* [debounce <-> throttle, distintUntilChanged, switch(Map), mergemap, map, mapto] 
* [combineLaetst(combine streams(observable) from two distint elements, similar to use zip in this case]
* [finally, endWith <-> startWith, subsrcibe, unsubscribe]
* [scan(similar to javascript array reduce)]
* [switchMap -> take only last observables available]
* [takeUntil -> unsubscribe observables that doesn't have unsubcribe method, used instead of unsubscribe, assert with value]
* [takeWhile -> listen to observable while conidtion is ture, assert with conditional statement]
* [zip -> pair different observables in sequence, new observable array with values of them in sequence]
* [forkjoin -> similar to zip but wait for the api to complete, useful for using two different async api]
* [catchError -> similar to handle error in promise]
* [retry -> used for error handle with catchError, execute code until specific time of error happens again]

* combineLatest and zip compare

`
endpoint_stream.combineLatest(id_stream) / only one of them is necessary -> map(data => makeRequest(data[0], data[1])
endpoint_stream.zip(id_stream) / both of them are required -> map(data => makeRequest(data[0], data[1])
`

* zip and forkJoin compare(forkJoin should be used with caution, similar to Promise.all), -> https://www.learnrxjs.io/operators/combination/forkjoin.html


`
ex) zip(Rx.observable.of([1, 2, 3]), Rx.observable.of(4, 5, 6)), forkJoin(Rx.observable.of([1, 2, 3]), Rx.observable.of(4, 5, 6).delay(2000)) 
`


* catchError and Retry 

`
ovservable.catch((e) => errorHandle(e)).retry(2)
`



## Rxjs Subject(relevant to hot cold observable, connect(), multicast etc)

 * It can be used in the same way with Observables, but it has more features such as code below
 * It can be used operator multicast() -> That pass values to multiple subscribers except multiple same side effects

___
const subject = new Rx.subject()

const subA = subject.subsrcibe((val) => from subA: print(val));
const subB = subject.subsrcibe((val) => from subB: print(val));

subject.next("First Value")
setTimeout(() => {
   subject.next("Next Value")
}, 1000)

-> from subA: First Value, from subB: First Value => from SubB: Next Value, from subB: Next Value
 
 const observable = Rx.observable.fromEvent(document, "click");
 
 const click = observable.do( _ => print("click one time"));
 
 const subject = click.multicast(() => new Rx.subject());
 
 const subA = subject.subscribe( c => print("subA: ", c.timeStamp));
 const subB = subject.subscribe( c => print("subB: ", c.timeStamp));
 
 subject.connect(); -> subA, SubB -> show same value
 
-> Click One Time, subA: ${timeStamp}, subB: ${timeStamp} =>  Click One Time, subA: ${otherTimeStamp}, subB: ${otherTimeStamp} 
 (show side effect message just once for each event) 
___


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
