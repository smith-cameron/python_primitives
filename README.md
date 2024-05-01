## Data Types
how a given value/data is classified and stored
### [Primitives](https://login.codingdojo.com/m/506/12457/87300)
[DOCS - Built In Types](https://docs.python.org/3/library/stdtypes.html#typesseq-rNumericTypes)
### [Variables](https://login.codingdojo.com/m/506/12457/87698) 
#### Reserved Python Keywords
These keywords are used for various purposes in Python, such as 
- defining control structures (e.g., `if`, `else`, `while`), 
- defining functions and classes (e.g., `def`, `class`), 
- Boolean values (e.g., `True`, `False`).
If you try to use a reserved keyword as a variable name, you will receive a syntax error.
```python
False    class    finally  is       return
None     continue for      lambda   try
True     def      from     nonlocal while
and      del      global   not      with
as       elif     if       or       yield
assert   else     import   pass
break    except   in       raise
```
#### [Numbers](https://login.codingdojo.com/m/506/12457/87301)
DOCS - Numeric Types — [`int`](https://docs.python.org/3/library/functions.html#int "int"), [`float`](https://docs.python.org/3/library/functions.html#float "float"), [`complex`](https://docs.python.org/3/library/functions.html#complex "complex")
##### __Integers__ (whole numbers)
```python
x = 5
print(type(x))
# <class 'int'>
```
##### __Float__ or Floating point numbers (commonly known as decimal numbers)
```python
num = 160.22
print(type(num))
# <class 'float'>
print(num)
# 160.22
```
##### __Complex__ numbers
are a part of the real number system and are often referenced with the letter j.  ex. 1 + 3j. Imaginary numbers. _If you accidentally generate one just round it up_
#### [Strings](https://login.codingdojo.com/m/506/12457/87302) (Literal Text)
Any sequence of characters (letters, numerals, ~($/}\#, etc...) enclosed in __single__ or __double__ quotes

```python
x = "hello"
print(type(x))
# <class 'str'>
```

Like many other popular programming languages, strings in Python are arrays of bytes representing Unicode characters. 
_However_, Python does not have a unique "character" data type, a single character is simply a string with a length of 1
```python
char = 'a'
print(len(char),type(char))
# 1 <class 'str'>
```
Perform math operators on them
```python
"Hello" * 5
# 'HelloHelloHelloHelloHello'
```
##### Concatenation
```python
mystring = 'this is a "string"?'
response = 'Yes'
print(mystring,response)
# this is a "string"? Yes
print(mystring+response)
# this is a "string"?Yes
```

#### Boolean
Assesses/represents the truthiness value of something. 
	(Data type returned from some expressions)
Or the direct value of a variable
It has only two values: __True__ and __False__ (note the uppercase T and F)
```python
print(bool(5<2))
# False

print(bool(5>2))
# True

x = True
print(x)
# True
print(type(x))
# <class 'bool'>
```
##### Boolean Operations — `and`, `or`, `not`[](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not "Permalink to this headline")
These are the Boolean operations, ordered by ascending priority:

|Operation|Result|Notes|
|---|---|---|
|`x or y`|if _x_ is true, then _x_, else _y_|(1)|
|`x and y`|if _x_ is false, then _x_, else _y_|(2)|
|`not x`|if _x_ is false, then `True`, else `False`|(3)|

Notes:
1. This is a short-circuit operator, so it only evaluates the second argument if the first one is false.
2. This is a short-circuit operator, so it only evaluates the second argument if the first one is true.
3. `not` has a lower priority than non-Boolean operators, so `not a == b` is interpreted as `not (a == b)`, and `a == not b` is a syntax error.
#### Type Casting
to change a value's data type from one type to another
All Python objects have data type methods we can use to convert number types from one to another.
```python
int_to_float = float(35)
float_to_int = int(44.2)
int_to_complex = complex(35)
print(int_to_float)
print(float_to_int)
print(int_to_complex)
print(type(int_to_float))
print(type(float_to_int))
print(type(int_to_complex))
```
str() ->  int()
it has to be a number to treat it as a number
```python
char = 'a'
print(int(char))
#ValueError: invalid literal for int() with base 10: 'a'
```
- Also with an empty string
Numbers can be changed to strings
```python
num = 160.22
print(str(num))
160.22
print(type(str(num)))
<class 'str'>
```
### [String Interpolation](https://login.codingdojo.com/m/506/12457/87302) (formatting strings) 
__Injecting variable values__
==we will use mostly for urls==

- Type casting with concatenation
```python
print("Hello " + 42) # output: TypeError
print("Hello " + str(42)) # output: Hello 42
```

#### string.format() 
Most languages have something like this(outdated)
- pass in arguments in the order in which they should fill the {}
```python
first_name = "Cameron"
last_name = "Smith"
age = 34
```

```python
# Correct :
print("My name is {} {} and I am {} years old.".format(first_name, last_name, age))

# Incorrect: 
print("My name is {} {} and I am {} years old.".format(age, first_name, last_name))
```

#### F-Strings (Literal String Interpolation)
```python
first_name = "Cameron"
last_name = "Smith"
age = 34
print(f"My name is {first_name} {last_name} and I am {age} years old.")
```
Use this for print statements when debugging improves readability

#### MSC String Notes
##### Escaping
###### Apostrophes
```python
print('We're going skiing this winter.')
#SyntaxError: invalid syntax
```
Python thinks the string ends after 'We', so everything after it is considered a syntactical error. You can use the backslash (`\`) sign to escape any string character:
```python
print('We\'re going skiing this winter.')
#output: We're going skiing this winter.
```
###### Curly Braces:
If you want to include curly braces as literal characters in the string, you can escape them by doubling them `{{` and `}}`.
###### Using `\` a literal character
When you may want to use backslash as it is often used as a literal character in strings - for example, to represent a file path or url
```python
print('C:\Users\Bob')
# SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in position 2-3: truncated \UXXXXXXXX escape
```
- **raw string** - Write `r` before the first quotation mark.
- **double backslash** - This will essentially escape the escape character.
```python
print(r'C:\Users\Bob')
print('C:\\Users\\Bob')
```
These two apply both for strings surrounded with single and double quotes.
##### Double Quotes
__Best Practice__: Use double quotes for 
- natural language messages
-  string interpolations
-  whenever you know there will be single quotes within the string
```python
name = 'Bob'

# Natural language
print("It is easy to get confused with single and double quotes in Python.")

# String interpolation
print(f"{name} said there will be food.")

# No need to escape a character
print("We're going skiing this winter.")

# Quotation inside a string
print("My favorite quote from Die Hard is 'Welcome to the party, pal'")
```
Freely embed quotations into strings surrounded by double quotation marks. 
No need to escape a character as with single quotes.
**==Note==**: you can’t use double quotes again in a string surrounded by double quotes. Doing so will result in the same syntax error as with single quotes:
```python
print("You can't use "double quotes" inside this string.")
# SyntaxError: invalid syntax. Perhaps you forgot a comma?
print('You can use "double quotes" like this.')
# output: You can use "double quotes" like this.
```
##### Python Single vs. Double Quotes PEP8
According to [PEP8](https://www.python.org/dev/peps/pep-0008/#string-quotes):
- PEP doesn’t make a recommendation on whether to use single or double quotes - pick a rule and stick to it.
- When a string is surrounded with single quotes, use double quotes inside it to avoid backslashes.
- When a string is surrounded with double quotes, use single quotes inside it to avoid backslashes.
- When using triple quoted strings, always use double quote characters inside it.
##### Single vs. Double Quotes Best Practices
Best practices for __single quoted__ strings:
- Make sure the string is somewhat short, or you’re dealing with a string literals
- Make sure there are no single quotations inside the string, as adding escape characters has a toll on readability.

Best practices for __double quoted__ strings:
- Use double quotes for text and string interpolation.
- Use double quotes when there’s a quotation inside a string - you can easily surround the quotation with single quotes.
##### Triple Quotes
- You can use both single and double quotes inside them.
- You can split the string into multiple lines.
- They are considered as a best practice when writing docstrings.
```python
print("""Triple quote string example 1""")
print('''Triple quote string example 2''')

print("""Here's a string I'll split into
mulitple 
lines.""")

print("""You can use 'single quotes' and "double quotes" inside!""")
```
