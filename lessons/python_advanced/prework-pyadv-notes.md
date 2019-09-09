### REGEX - Python regular expressions

(in assessment but not in lecture materials in this folder)

* https://developers.google.com/edu/python/regular-expressions

Regular expressions are a powerful language for matching text patterns. The Python "re" module provides regular expression support.

In Python a regular expression search is typically written as:
```match = re.search(pat, str)```

The re.search() method takes a regular expression pattern and a string and searches for that pattern within the string. If the search is successful, search() returns a match object or None otherwise. Therefore, the search is usually immediately followed by an if-statement to test if the search succeeded.

The power of regular expressions is that they can specify patterns, not just fixed characters

Example:

```
## Search for pattern 'iii' in string 'piiig'.
  ## All of the pattern must match, but it may appear anywhere.
  ## On success, match.group() is matched text.
  match = re.search(r'iii', 'piiig') # found, match.group() == "iii"
  match = re.search(r'igs', 'piiig') # not found, match == None

  ## . = any char but \n
  match = re.search(r'..g', 'piiig') # found, match.group() == "iig"

  ## \d = digit char, \w = word char
  match = re.search(r'\d\d\d', 'p123g') # found, match.group() == "123"
  match = re.search(r'\w\w\w', '@@abcd!!') # found, match.group() == "abc"
  ```
