### Python file handling (open, read, write) tutorial:
https://www.w3schools.com/python/python_file_handling.asp

* add header to CSV file in Python: https://stackoverflow.com/questions/20347766/pythonically-add-header-to-a-csv-file

* writing a dictionary from csv: https://docs.python.org/3/library/csv.html#csv.DictWriter

### REGEX - Python regular expressions

(in assessment but not in lecture materials in this folder)

* https://developers.google.com/edu/python/regular-expressions

*problem: Dict and Files page last updated 2016, methods such as 'U' in read 'rU' already deprecated*

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

-----------

Emails Example:

Suppose you want to find the email address inside the string 'xyz alice-b@google.com purple monkey'. Here's an attempt using the pattern r'\w+@\w+':

```
  str = 'purple alice-b@google.com monkey dishwasher'
  match = re.search(r'\w+@\w+', str)
  if match:
    print match.group()  ## 'b@google'
```    
   
The search does not get the whole email address in this case because the \w does not match the '-' or '.' in the address. We'll fix this using the regular expression features below.


Square Brackets

Square brackets can be used to indicate a set of chars, so [abc] matches 'a' or 'b' or 'c'. The codes \w, \s etc. work inside square brackets too with the one exception that dot (.) just means a literal dot. For the emails problem, the square brackets are an easy way to add '.' and '-' to the set of chars which can appear around the @ with the pattern r'[\w.-]+@[\w.-]+' to get the whole email address:

```
  match = re.search(r'[\w.-]+@[\w.-]+', str)
  if match:
    print match.group()  ## 'alice-b@google.com'
```

You can also use a dash to indicate a range, so [a-z] matches all lowercase letters. To use a dash without indicating a range, put the dash last, e.g. [abc-]. An up-hat (^) at the start of a square-bracket set inverts it, so [^ab] means any char except 'a' or 'b'.



**findall**
findall() is probably *the single most powerful function in the re module*. Above we used re.search() to find the first match for a pattern. findall() finds *all* the matches and returns them as a list of strings, with each string representing one match.

```
  ## Suppose we have a text with many email addresses
  str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'

  ## Here re.findall() returns a list of all the found email strings
  emails = re.findall(r'[\w\.-]+@[\w\.-]+', str) ## ['alice@google.com', 'bob@abc.com']
  for email in emails:
    # do something with each found email string
    print email
```

**findall With Files**

For files, you may be in the habit of writing a loop to iterate over the lines of the file, and you could then call findall() on each line. Instead, let findall() do the iteration for you -- much better! Just feed the whole file text into findall() and let it return a list of all the matches in a single step (recall that f.read() returns the whole text of a file in a single string):

```
  # Open file
  f = open('test.txt', 'r')
  # Feed the file text into findall(); it returns a list of all the found strings
  strings = re.findall(r'some pattern', f.read())
```

--------------
practice: 
https://www.hackerrank.com/domains/regex
