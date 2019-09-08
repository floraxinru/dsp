## Python Part 1 Assessment Notes

### Lambda

### Map
https://realpython.com/python-lambda/#map
> The built-in function map() takes a function as a first argument and applies it to each of the elements of its second argument, an iterable. Examples of iterables are strings, lists, and tuples. 

map() returns an iterator corresponding to the transformed collection. As an example, if you wanted to transform a list of strings to a new list with each string capitalized, you could use map(), as follows:

```list(map(lambda x: x.capitalize(), ['cat', 'dog', 'cow']))```
```
['Cat', 'Dog', 'Cow']
```

