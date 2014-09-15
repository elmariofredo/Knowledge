# Control Flows

Concepts behind program control flow.

##❯ Callbacks
##❯ Promises
##❯ Events
##❯ Streams
##❯ Functional reactive programming

Example:

```javascript
var up   = $('#up').asEventStream('click');
var down = $('#down').asEventStream('click');
​
var counter =
  // map up to 1, down to -1
  up.map(1).merge(down.map(-1))
  // accumulate sum
    .scan(0, function(x,y) { return x + y });
​
// assign observable value to jQuery property text
counter.assign($('#counter'), 'text');
```

References: https://baconjs.github.io https://en.wikipedia.org/wiki/Functional_reactive_programming

##❯ Communicating sequential processes

References: http://jlongster.com/Taming-the-Asynchronous-Beast-with-CSP-in-JavaScript http://en.wikipedia.org/wiki/Communicating_sequential_processes

##❯ Generator-based

References: https://github.com/jmar777/suspend
