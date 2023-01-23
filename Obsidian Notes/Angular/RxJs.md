## Operators

[RxJS Marbles](https://rxmarbles.com/)

- map
	```javascript
	import { fromEvent, interval, withLatestFrom } from 'rxjs';
	const clicks = fromEvent(document, 'click');
	const timer = interval(1000);
	const result = clicks.pipe(withLatestFrom(timer));
	result.subscribe(x => console.log(x));
	```

- combineLatest
	returns array of values from different observables
	This can be used to return data of selector and network call to next stage

- switchMap
	gives access to the previous observable stream
	But also it will discard the current activity within it if the previous stream changes

- concatMap
	To overcome above limitation concatMap is used
	It stacks all the new stream and perform activity on current stream and them move to the next

- filter
	Filter the stream, if it has nothing to return then the next stage will not run.

- tap
	It's used to perform side effects without affecting the current stream

- catchError
	It's really important when you are performing any network call in any operator, if the error not catched then it will destroy the entire stream
	return EMPTY or throwError

- retryWhen

- concat

- of
	It convert plain data into stream observables

- pipe
	It allows to modify stream in multiple stages by using RxJS operators as each stage

