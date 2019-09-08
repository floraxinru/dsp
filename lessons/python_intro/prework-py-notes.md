## Python Part 1 Assessment Notes

### Lambda

Example:

```lambda x: x + 1```

Where: the keyword: lambda
A bound variable: x + 1
A body: x

Note: In the context of this article, a bound variable is an argument to a lambda function.

You can apply the function above to an argument by surrounding the function and its argument with parentheses:
``` (lambda x: x + 1)(2)```
>>> 3


### Map
https://realpython.com/python-lambda/#map
> The built-in function map() takes a function as a first argument and applies it to each of the elements of its second argument, an iterable. Examples of iterables are strings, lists, and tuples. 

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
