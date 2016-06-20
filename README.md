# reInterval
![TRAVIS](https://travis-ci.org/4rzael/reInterval.svg)

[![NPM](https://nodei.co/npm/reinterval.png?downloads=true&downloadRank=true)](https://nodei.co/npm/reinterval/)

Reschedulable setInterval for node.js.

###### Note: Work highly inspired by [mcollina](https://github.com/mcollina)'s [retimer](https://github.com/mcollina/retimer).

## Example

```js
var reInterval = require('reInterval');

var inter = reInterval(function () {
  console.log('this should be called after 13s');
}, 10 * 1000);

// This will reset/reschedule the interval after 3 seconds, therefore
// the interval callback won't be called for at least 13 seconds.
setTimeout(function () {
  inter.reschedule(10 * 1000);
}, 3 * 1000);
```


## API:

`reInterval(callback, interval[, param1, param2, ...])`

This is exactly like setInterval.

arguments:
  - `callback`: The callback to be executed repeatedly.
  - `interval`: The number of milliseconds (thousandths of a second) that the `reInterval()` function should wait before each call to `callback`.
  - `param1, param2, ...`: *(OPTIONAL)* These arguments are passed to the `callback` function.

**returns an `interval` object with the following methods:**

`interval.reschedule([interval])`

This function resets the `interval` and restarts it now.

arguments:
  - `interval`: *(OPTIONAL)* This argument can be used to change the amount of milliseconds to wait before each call to the `callback` passed to the `reInterval()` function.

`interval.destoy()`

This function clears the interval.

Note: This will also clear the `callback` and `params` passed to reInterval, so calling this essentially just makes this object ready for overwriting with a new `interval` object. Please ensure this function is called before overwriting the object, because the interval can continue to run in the background unless cleared.

## license

**MIT**
