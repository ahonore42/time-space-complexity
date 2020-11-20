# Optimizing our code with Big O Notation
<div>
  <img src="https://i.redd.it/voghw477i8y41.png" alt='bigo' />
</div>

## Introduction
What is `Big O`?

As software engineers, we should be concerned with the performance of the code we are writing. In an ideal world, we'd like for our algorithms and application architectures to be both efficient and performative, however, some algorithms are more efficient than others. In determining whether or not our code is *scalable* it may be difficult to communicate the costs in terms of time and space complexity due to variations in machine run speeds and performance, but that is precisely where Big O notation comes in handy.

`Big O` is a **simplified analysis of an algorithm's efficiency**. An `algorithm` is little more than a series of steps required to perform some task. If we treat each step as a basic unit of computation, then an algorithm’s execution time can be expressed as the number of steps required to solve the problem. Examples: `O(1), O(log(n)), O(n), O(n log(n)), O(n^2)`
- The O stands for the Order of `time` and `space` complexity. 
- In Big O notation, `n` stands for the complexity in terms of `input size` in a function or algorithm. Typically, input size is dominated by the largest factor of `n` in an algorithm.
- Big O is machine independent since it examines the basic computer steps involved in an algorithm.
- After you have implemented any solution for an algorithm, it is best to then refactor your solution to account for Big-O time and space complexity.

### Valuable Big O and Algorithm Resources (Bookmark These)
- https://www.bigocheatsheet.com/
- https://bradfieldcs.com/algos/analysis/big-o-notation/
- https://www.codewars.com/
- https://leetcode.com/


## What does better mean in terms of code?
- Faster (time complexity)
- Less memory-intensive (space complexity)
- More readable / legibility

These are all factors we can try and optimise, but generally the **`speed that your code runs`** can be considered the most important factor, _so how do we evaluate speed_?

### The problem with time
- Different machines will record different times
- The same machine will record different times!
- For fast algorithms, speed measurements may not be precise enough
- To solve this, we measue algorithmic efficiency in Big-O notation.

# Measuring Big O
<div>
  <img height="400" src="https://devopedia.org/images/article/17/4996.1513922020.jpg" alt="graph" />
</div>

Big-O time and space complexities for an algorithm will typically fall into one of these categories (if not, it should be refactored):
| **Big O**       | **Definition**      | **Function Behavior** |
| :-------------- |:--------------------| :----------------------------------------------------------|
| O(1)      	  | Constant Time       | Always executes in the `same time` regardless of the size of the input data set |
| O(log(n))       | Logarithmic Time    | Runs proportionally to the logarithm of the input data size (faster than linear time!) |
| O(n)            | Linear Time         | Time complexity will grow in direct proportion to the size of the input data |
| O(n log(n))     | Log-Linear Time     | Time complixity grows as the product of linear and logarithmic time  |
| O(n^2)          | Quadratic Time      | Performance is directly proportional to the squared size of the input data set |
| O(2^n)          | Exponential Time    | Growth doubles with each additon to the input data set, rising at an ever-increasing rate |
| O(n!)           | Factorial Time      | Absolute worst case scenario, complexity grows at a factorial rate with data input size |

## Examples
Lets take a look at a couple of examples. Here is an answer to one of the questions from homework on day two.

```jsx
function addUpTo(n) {
	let total = 0;
	for (let i = 1; i <= n; i++) {
		total += i;
	}
	return total;
}
console.log(addUpTo(6))
```
This problem has a time complexity of `O(n)` because the output of the function will increase at the same rate as the input of n inputs.

An alternate way to solve this same problem. 

```jsx
function addUpTo(n) {
	return n * (n + 1) / 2;
}
```
This is more of a mathematical solution & we're not going to get stuck on the semantics of why it works. 
The time complexity of this solution is `O(1)`

## A Rule Of Thumb
A general way that we can determine the speed of a function is by **`adding up all the operators`**.

The example has many operators and some of these operators are n, so to generalize the number of operators generally grows at the rate of n
The 2nd example only has three operators.


## Big O Definition 
We say that an algorithm is O(f(n)) if the number of simple operators the computer has to do is eventually less than a constant times f(n), as n increases

- f(n) could be linear (f(n) = n)
- f(n) could be quadrratic (f(n) = n^2)
- f(n) could be constant (f(n) = 1)
- f(n) could be something entirely different!

We're talking about the **worst case scenario** with big O notation


## So the examples above
Time complexity is always the same, `O(1)` because the number of operations is (eventually) bounded by a multiple of `n(say, 10n)` is `O(n)`

<img height="400" src="https://user-images.githubusercontent.com/29616227/65440287-7f5ceb00-ddf6-11e9-9409-49c5185a2c07.jpg">


Lets check out the time complexity of the for loop we used to create our card game.

- A for loop gives us a time complexity of `O(n)`
- A nested for loop gives us a `O(n)` time complexity inside of a `O(n)` time complexity, which gives us `O(n^2)`, which is a significant difference...

### Nested for loop O(n^2) 
```jsx
function printAllPairs(n) {
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
      console.log(i, j);
    }
  }
}
```

If n is 2 then we have 4 pairs, if n is 3 then we have 9 pairs... 4 becomes 16 pairs... 

It begins to grow very steep... an exponential curve. 


## Big O Shorthand
Here are some ways we can get a rough picture of the time complexity of the function we learnt last week.

Constants don't matter...
1. Arithmetic operations are constant

2. Variable assignment is constant 

3. Accessing elements in an array (by index) or object (by key) is constant

4. In a loop, the complexity is the length of the loop times the complexity of whatever happens inside of the loop

5. The largest subset of complexity (worst case scenario) within the function's operations takes priority


 ### Determine the time complexity for the following function(5 mins)
```jsx
function logUpTo(n) {
    for (let i = 1; i <= n; i++) {
        console.log(i)
    }
}


function logAtMost10(n) {
    for (let i = 1; i <= Math.min(n, 10); i++) {
        consoe.log(i)
    }
}

function logAtLeast10(n) {
    for (let i = 1; i <= Math.max(n, 10); i++) {
        console.log(i)
    }
}

function onlyElementsAtEvenIndex(array) {
    let newArray = Arr(Math.ceil(array.length / 2));
    for (let i = 0; i < array.length; i++) {
        if (i % 2 === 0) {
            newArray[i / 2] = array[i];
        }
    }
    return newArray;
}

function subtotalArray(array) {
    let subtotalArray = Array(array.length);
    for (let i = 0; i <= array.length; i++) {
        let subtotal = 0;
        for (let j = 0; j <= i; j++) {
        subtotal += array[j];
    }
    subtotalArray[i] = subtotal;
}
return subtotalArray;

}

```

## Space complexity
Another complexity to take into consideration when writing code.

Rules of thumb...
- Most primitives (booleans, numbers, undefined, null) are constant space.
The size of the input doesn't matter - if the input is 5 or 1000 it doesn't matter 
- Strings require O(n) space (where n is the string length) 
Grows as the length of the string grows
- Reference types are generally O(n), where n is the length (for arrays) or the number of keys (for objects)

Example of `O(1)` space complexity
``` jsx
function sum(arr) {
    let total = 0;
    for (let i = 0; i < arr.length; i++) {
        total += arr[i];
    }
    return total;
}
```

Example of `O(n)` space complexity
``` jsx
function double(arr) {
    let newArr = [];
    for (let i = 0; i < arr.length; i++) {
        newArray.push(2 * arr[i]);
    }
    return newArray;
}
 ```