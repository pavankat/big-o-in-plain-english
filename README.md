# Algorithms & Big O Notation in Plain English

### What are algorithms? 

Algorithms are basically functions.

With functions that are algorithms

* you take in arguments.

* you explicitly return values.

#####g 1.1 Example of an algorithm

algorithm that counts the number of vowels in a word and returns the count.

```
function countVowels(word){
	var vowels = ['a', 'i', 'e', 'o', 'u'];
	var count = 0;
	for (var i=0; i<word.length; i++){ count++; }
	return count;
}

```

### When are functions not algorithms?

When you write a function it may or may not

* have arguments

* return a value

Functions that don't take arguments or return a value are usually used to dry up repetitive code, print something to the screen or serve as an argument to be executed later

#####g 1.2 Example of a function that is not an algorithm

an anonymous function that gets passed to jQuery's on function. 

```
		$('button').on('click', function(){ 
			alert('hi') 
		});
```

#####g 1.3 Example of a function that is not an algorithm

This function has no arguments, no return

```
		function clearDiv(){
			$('#div').html("");
		}
```
#####g 1.4 Example of a function that is not an algorithm

This function has an argument, but no return

```
		function clearDiv(text){
			$('#div').text(text);
		}
```

### What is Big O?

Big O is short for Big O Notiation.

Big O is how programmers talk about algorithms.

An algorithm's Big O Notation is determined by how long the algorithm takes to return output in the **worst case scenario**.

The math term for the **worst case scenario** is **"upper bound"**.

Example: if I gave an algorithm an array of 1000 items, it would run slower than if I gave the algorithm an array of 10 items.

### How do you say O(n)

O(n) reads as "Order of N" or short for "O of N".

the O function is the Order function.

### Why is it called Big O?

Because we're dealing with orders of magnitude.

### Why is Big O important? 

Orders of magnitude are important.

Imagine you're buying a car and you have two options.

a super car that costs $100k and a sedan that costs $10k.

The cost difference between the super car and the sedan is pretty huge 

BUT in approximation, as long as you're within an order of magnitude, you're pretty close. 

Another example: Let's say there are 50 gumballs in a gumball machine. You guess 500. That's pretty off, but in approximation you're not that off. If you guessed 5000 then you'd be way off.

## Dive into O(1)

#####g Example 2.1

```
function returnItem(item){
	return item;
}
```

returnItem is a pointless function. but bear with me.

```
returnItem(2);
```

returnItem's Big(O) is constant time. No matter what we pass to returnItem, the algorithm will go through one unit of work.

The "complexity" of this function is O(1).

If you want to graph O(1) then you would set y equal to 1 and graph it.

**y = 1**

![o(1)](o_1__plot.png)

Notice that the further right of the horizontal axis (x axis) you go, the vertical axis (y axis) stays the same.

## Dive into O(n)

#####g Example 2.2
```
function itemInList(check, list){
	for (var i=0; i<list.length; i++){
		if (list[i] == check) return true;
	}
	return false;
}
```

This will run pretty quick:

```
itemInList(2, [1,2,3]);
```

The "complexity" of itemInList is O(n)

This means that it's a linear graph

For itemInList, if the length of the array is 3, **worst case** it'll take 3 units of work.

Sure, in the best case it'll take 1 unit of work, but Big O Notation isn't about the best case scenario, it's about the **worst case scenario**.

If you want to graph O(n) then you would replace the n with a x and set it equal to a y.

**y = x**

![o(n)](o_n__plot.png)

Notice that the further right of the horizontal axis (x axis) you go, the vertical axis (y axis) goes up too.

## Dive into O(n^2)

##### Example 2.3
```
function allCombos(list){
	var results = [];
	for (var i=0; i<results.length; i++){
		for (var j=0; j<results.length; j++){
			results.push([i, j]);
		}
	}
}
```

If we do allCombos([1,2,3]) we'd get back [(1,1) (1,2), (1,3), (2, 1), (2, 2), (2, 3), (3, 1), (3, 2), (3, 3)].

The "complexity" of allCombos is O(n^2)

The list argument of allCombos is the n in O(n^2)

allCombos([1]) -> [[1,1]]. One unit of work.  1^2 = 1
allCombos([1,2]) -> [[1,1], [1,2], [2,1], [2,2]]. Four units of work. 2^2 = 4

So n * n is n^2.

## Comparison of O(1), O(n), O(n^2)

Notice that the further right of the horizontal axis (x axis) you go, the vertical axis (y axis) goes up fastest for O(n^2), slower for O(n) and constant for O(1).

This means that O(n^2) runs slower than O(n), which runs slower than O(1).

![comparison](runtime_comparison.png)


## Dive into O(log(n))

O(1) < O(n) < O(log(n)) < O(n^2)

#####g What does an algorithm look like that has a Big O of O(log(n))?

The choice of the next element on which to perform some action is one of several possibilities, and only one will need to be chosen.

#####g Ex. Looking up people in a phone book is O(log(n))

You don't need to check every person in the phone book to find the right one; instead, you can simply divide-and-conquer, and you only need to explore a tiny fraction of the entire space before you eventually find someone's phone number.

Of course, a bigger phone book will still take you a longer time, but it won't grow as quickly as the proportional increase in the additional size.

##### Ex. an algorithm that has a Big O of O(log(n))

```
function logn(x){
	while (x > 0) x/=2;
	return x;
}
```

Iteration |   x
----------|--------
    0     |  x (this is the same thing as x/1)
    1     |  x/2
    2     |  x/4
   ...    |  ...
   ...    |  ...
    k     |  x/2^k 

2^k = x → Applying log to both sides → k = log(x)

log(2^k) = log(x)

k*log(2) = log(x)

k = log(x)/log(2)

k approximately equals log(x)

![o(log n)](o_logn.gif)

## O(n log n)

to do: convert to JS and add explanation

```
int result = 0;
foreach (int num in numbers)
{
    int index = numbers.length - 1;
    while (index > 1)
    {
        // yeah, stupid, but couldn't come up with something more useful :-(
        result += numbers[index];
        index /= 2;
    }
}
return result;
```

## O(1) vs O(n) vs O(n^2) explained without code

##### O(1)
Consider single-digit addition with a pencil and paper. The kind you learned when you were young.

```
5+5 = 10

3+3 = 6

2+2 = 4

2+3 = 5

6+7 = 13
```

Each of those different problems took the same # of operations to complete (or the same amount of units of work to complete). You take one number and add it to another. Done.

Because it's always the same units of work to complete, no matter what the problem, the Big O is constant, this is an example of O(1).

##### O(n)

Consider multi-digit addition with a pencil and paper. 

```
55+72 = 127

455+322= 777

1234+4447= 5681

4999 + 56 = 5055
```

Notice how the number of operations (or the amount of units of work to complete) goes up as the number of digits go up.

The number of operations directly correlate (are one to one) with the number of digits of the biggest number being added.

This would take worst case O(n) units of work.

##### O(n^2)

Now, consider multi-digit multiplication with pencil and paper.

```
55538*92338 = 5128267844
```

This is much harder to do than the previous two asks. 

Each digit of the bottom number has to be multiplied by each digit in the top number.

If you were multiplying 100 digit numbers by each other then it would take 10,000 mathematical operations to complete (units of work to complete).

This would take worst case O(n^2) units of work to complete.

## How to calculate Big O?

Often you don't need math to figure out what the Big-O of an algorithm is but you can simply use your intuition. 

If your code uses a single loop that looks at all n elements of your input, the algorithm is O(n). 

If the code has two nested loops, it is O(n^2).

Three nested loops gives O(n^3), and so on.

## Big O can be misleading

Big-O notation is an estimate and is only useful for large values of n. 

##### insertion sort vs merge sort

The worst-case running time for the **insertion sort algorithm is O(n^2)**. 

Relative to Big O that is worse than the running time for **merge sort, which is O(n log n)**. 

But for small amounts of data (when n is small), insertion sort is actually faster, especially if the array is partially sorted already!

Big O is useful when comparing two algorithms to figure out which one runs faster for when n is large.

If the amount of data (n) is relatively small, then even a slow algorithm will be fast enough for practical use.

## Other Big O Categories from fastest to slowest

Big-O | Name | Description
------| ---- | -----------
**O(1)** | constant | **This is the best.** The algorithm always takes the same amount of time, regardless of how much data there is. In other words, the number of units of work it takes the algorithm to complete is independent of the size of the input. Example: looking up an element of an array by its index.
**O(log n)** | logarithmic | **Pretty great.** These kinds of algorithms remove a percentage of the amount of data to sift through with each iteration. If you have 100 items, it takes about 7 steps to find the answer. With 1,000 items, it takes 10 steps. And 1,000,000 items only take 20 steps. This is super fast even for large amounts of data. 
**O(n)** | linear | **Good performance.** If you have 100 items, this does 100 units of work. This is usually the case for a loop. If you double the size of n, then the algorithm does 2 * n units of work.
**O(n log n)** | "linearithmic" | **Decent performance.** This is slightly worse than linear but not too bad. Example: the fastest general-purpose sorting algorithms.
**O(n^2)** | quadratic | **Kinda slow.** If you have 100 items, this does 100^2 = 10,000 units of work. Doubling the number of items makes it four times slower (because 2 squared equals 4). Example: a double for loop -> you have to look at every pair of input elements.
**O(n^3)** | cubic | **Poor performance.** If you have 100 items, this does 100^3 = 1,000,000 units of work. Doubling the input size makes it eight times slower. Example: matrix multiplication. Or, you're looking at every pair of inputs but the operation you do requires looking at all of the inputs again
**O(2^n)** | exponential | **Very poor performance.** You want to avoid these kinds of algorithms, but sometimes you have no choice. Adding just one bit to the input doubles the running time. Example: traveling salesperson problem.
**O(n!)** | factorial | **Intolerably slow.** It literally takes a million years to do anything. Example: you need to consider every possible subset of your inputs.

![o(n)](most-of-them.png)

## Resources used

https://justin.abrah.ms/computer-science/big-o-notation-explained.html

https://github.com/raywenderlich/swift-algorithm-club/blob/master/Big-O%20Notation.markdown

http://stackoverflow.com/questions/17122807/big-o-ologn-code-example

https://www.quora.com/How-would-you-explain-O-log-n-in-algorithms-to-1st-year-undergrad-student

http://stackoverflow.com/questions/9223351/confused-on-big-o-notation?rq=1

http://stackoverflow.com/questions/107165/big-o-for-eight-year-olds?rq=1


## Other Resources

http://www.daveperrett.com/articles/2010/12/07/comp-sci-101-big-o-notation/

http://stackoverflow.com/questions/2307283/what-does-olog-n-mean-exactly

https://medium.freecodecamp.com/my-first-foray-into-technology-c5b6e83fe8f1#.s488n2g0j

https://medium.freecodecamp.com/time-is-complex-but-priceless-f0abd015063c#.x22db1a69

http://adrianmejia.com/blog/2014/02/13/algorithms-for-dummies-part-1-sorting/

http://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation

http://bigocheatsheet.com/

https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/
