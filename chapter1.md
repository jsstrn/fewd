# Problem Set 1

## Problem

Create three buttons labelled 1, 2, and 3, respectively. When a user clicks on any of these buttons you should print to the console its corresponding number.

Your solution should be written in JavaScript. You may **not** use HTML or CSS in this exercise.

## Solution

Let's explore a few ways to solve this problem.

### The naive approach

Of course we can opt for the naive approach, which is to create one button and then duplicate our code to create the rest of the buttons.

❔ This approach certainly solves the problem, but can you think of any reasons why this might not be a good idea?

```
var btn1 = document.createElement('button')
btn1.textContent = 1
btn1.addEventListener('click', function () {
  console.log(n)
})
document.body.appendChild(btn1)

var btn2 = document.createElement('button')
btn2.textContent = 1
btn2.addEventListener('click', function () {
  console.log(n)
})
document.body.appendChild(btn2)

var btn3 = document.createElement('button')
btn3.textContent = 1
btn3.addEventListener('click', function () {
  console.log(n)
})
document.body.appendChild(btn3)
```

### Using a `for` loop

Another way would be to use a `for` loop that iterates over the elements in an array.

```
var numbers = [1, 2, 3]
for (var i = 0; i < numbers.length; i++) {
  var n = numbers[i]
  var el = document.createElement('button')
  el.textContent = n
  el.addEventListener('click', function () {
    console.log(n)
  })
  document.body.appendChild(el)
}
```

❔ The problem is that all our buttons now print the same value to the console. Why does this happen and how can we resolve it?

```
for (var i = 0; i < numbers.length; i++) {
  var n = numbers[i]
  var el = document.createElement('button')
  el.textContent = n
  el.addEventListener('click', (function (number) {
    return function () {
      console.log(number)
    }
  })(n))
  document.body.appendChild(el)
}
```

In the next segment we'll explore another way to solve this using the `forEach` method.

### Using the `forEach` method

In JavaScript, `Array.prototype.forEach()` executes a given function once for each element in the array.

```
var numbers = [1, 2, 3]
numbers.forEach(function (n) {
  var el = document.createElement('button')
  el.textContent = n
  el.addEventListener('click', function () {
    console.log(n)
  })
  document.body.appendChild(el)
})
```
