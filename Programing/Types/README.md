# Types

##❯ Functional

##❯ Imperative

Telling the "machine" how to do something, and as a result what you want to happen will happen.

Example:

```javascript
var numbers = [1,2,3,4,5]
var total = 0

for(var i = 0; i < numbers.length; i++) {
  total += numbers[i]
}
console.log(total) //=> 15
```

References:
  http://latentflip.com/imperative-vs-declarative/


##❯ Declarative

Telling the "machine" what you would like to happen, and let the computer figure out how to do it. E.g. SQL is good example.

Example:

```SQL
SELECT * FROM `table`;
```

```javascript
var numbers = [1,2,3,4,5]

var total = numbers.reduce(function(sum, n) {
  return sum + n
});
console.log(total) //=> 15
```

References:
  http://latentflip.com/imperative-vs-declarative/
