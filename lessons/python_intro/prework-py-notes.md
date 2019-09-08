## Python Part 1 Assessment Notes


### Lambda
https://www.w3schools.com/python/python_lambda.asp
A lambda function is a small anonymous function.

A lambda function can take any number of arguments, but can only have one expression.

Syntax:
``` lambda arguments : expression```


Example:

```lambda x: x + 1```

Where: the keyword: lambda
A bound variable: x + 1
A body: x

Note: In the context of this article, a bound variable is an argument to a lambda function.

You can apply the function above to an argument by surrounding the function and its argument with parentheses:
``` (lambda x: x + 1)(2)```
> 3


### Map
https://realpython.com/python-lambda/#map
> The built-in function map() takes a function as a first argument and applies it to each of the elements of its second argument, an **iterable**. Examples of iterables are strings, lists, and tuples. 

map() returns an iterator corresponding to the transformed collection. As an example, if you wanted to transform a list of strings to a new list with each string capitalized, you could use map(), as follows:

```list(map(lambda x: x.capitalize(), ['cat', 'dog', 'cow']))```
```
['Cat', 'Dog', 'Cow']
```
You need to invoke list() to convert the iterator returned by map() into an expanded list that can be displayed in the Python shell interpreter.

Using a list comprehension eliminates the need for defining and invoking the lambda function:
```
[x.capitalize() for x in ['cat', 'dog', 'cow']]
```
```
['Cat', 'Dog', 'Cow']
```

#### Iterator vs. Iterable
An iterator is an object that contains a countable number of values.

An iterator is an object that can be iterated upon, meaning that you can traverse through all the values.

Technically, in Python, an iterator is an object which implements the iterator protocol, which consist of the methods __iter__() and __next__().

Lists, tuples, dictionaries, and sets are all iterable objects. They are iterable containers which you can get an iterator from.

All these objects have a iter() method which is used to get an iterator. Strings are also iterable; can use a for loop to iterate through characters of a string. The for loop actually creates an iterator object and executes the next() method for each loop.

https://www.w3schools.com/python/python_iterators.asp



### Filter
The built-in function filter() can be converted into a list comprehension. It takes a predicate as a first argument and an iterable as a second argument. It builds an iterator containing all the elements of the initial collection that satisfies the predicate function.

Example:

Here’s an example that filters all the even numbers in a given list of integers:

```even = lambda x: x%2 == 0```

```list(filter(even, range(11)))```
> [0, 2, 4, 6, 8, 10]


Note that filter() returns an iterator, hence the need to invoke the built-in type list that constructs a list given an iterator.

The implementation leveraging the list comprehension construct gives the following:

```[x for x in range(11) if x%2 == 0]```
> [0, 2, 4, 6, 8, 10]


### Reduce
As map() and filter(), its first two arguments are respectively a function and an iterable. It may also take an initializer as a third argument that is used as the initial value of the resulting accumulator. For each element of the iterable, reduce() applies the function and accumulates the result that is returned when the iterable is exhausted. 
https://realpython.com/python-lambda/#alternatives-to-lambdas 

--------------
### Python Datetime (useful!)
https://www.w3schools.com/python/python_datetime.asp


--------------
### Big-O Complexity

**Real-world examples:**
* O(1) - determining if a number is odd or even
* O(log N) - finding a word in the dictionary (using binary search)
* O(N) - reading a book
* O(N log N) - sorting a deck of playing cards (using merge sort)
* O(N^2) - checking if you have everything on your shopping list in your trolley
* O(10^N): trying to break a password by testing every possible combination (assuming numerical password of length N)

**How to find time complexity of an algorithm**(Read)
https://stackoverflow.com/questions/11032015/how-to-find-time-complexity-of-an-algorithm?rq=1

https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation?rq=1

https://stackoverflow.com/questions/3255/big-o-how-do-you-calculate-approximate-it
