# Python Basics

## Script
Let's start by making our first Python file.  

```python
# basics.py
x = input("Enter a letter: ")
print("You entered {}.".format(x))
```

A file such as this with a list of Python commands is call a script.

`# basics.py` is a comment line.  The symbol `#` indicates that everything that
follows on that line is a comment and should be ignored by the interpreter.

`x = input("Enter a letter: ")` types the given string and waits for the user
to type information followed by an enter.  What is typed is stored as a string
into the variable `x`.  In Python, you do not need to explicitly declare 
variable types.  Python will infer the variable type.

`print("You entered {}.".format(x))` prints the specified string to the
console.  In order to include the value of a variable in a string, we specify
where we want the variable to be included in the string using the `{}` 
placeholder.  Then, we specify the variable after the string by appending
`.format(x)` to the string.  

The script above can be run from the command line by typing `python basics.py`.

## Blocks and Indentations
Let's add an if statement to this code:
```python
# basics.py
x = input("Enter a letter: ")
print("You entered {}.".format(x))
if x == 'a':
    print("Add")
    a = 1
    b = 2
    c = a + b
    print("{} + {} = {}".format(a, b, c))
elif x == "s":
    print("Subtract")
    a = 1
    b = 2
    c = a - b
    print("{} - {} = {}".format(a, b, c))
else:
    print("{} not recognized".format(x))
print("Finished")
```
Blocks of code are identified using indentation, typically an indent of 4
spaces.  To indicate a new block should start after a command, we use the `:`.

Variable assignments are done using `=`.

Equality checking is done using `==`.
  
In the `if` statement above, if `x` contains the string `a`, it executes the
first block.  If `x` does not contain `a`, it will look at the next `elif`
statement.  If 'x' contains 's', it will execute the block following the
`elif`.  Finally, if neither the `if` or `elif` are true, the `else` block
will be run.

As the final print statement is not indented, it will be run after the `if` 
statement.  

## Functions in Modules
Long scripts can be hard to maintain and use.  It is desirable to break code
up into modular functions.

```python
# first_module.py
def add(a, b):
    c = a + b
    return c, "+"
    
def subtract(a, b):
    c = a - b
    return c, "-"

if __name__ == "__main__":
    a = 5
    b = 3
    answer, symbol = add(a, b)
    print("{} {} {} = {}".format(a, symbol, b, answer))
    answer, symbol = subtract(a, b)
    print("{} {} {} = {}".format(a, symbol, b, answer))
```

The `def` keyword defines a function with the name that is given after `def`.
After the function name, there must be a set of `()` followed by a `:`.  The
code for the function should then be indented.  Parameter variables can be 
sent to the function by including those inside the `()`.

A python file containing functions is generally called a module.  If you want
to run that module from the command line, Python
needs to know where the code should start in the module.  That is done by
the statement `if __name__ == "__main__"`.  When a module is being executed,
it has a special variable called `__name__`.  If the module was directly 
called from the command line, the variable `__name__` is given the value
`__main__`.  So, if the file was run from the command line, the 
`if __name__ == "__main__"` statement will be true and the code will start
there.

What are the advantages of running modular code?
* Testable (crucial for medical software design)
* Easier to read, can follow logic better
* Code reuse (once a function is tested and validated, it can be used again
without much thought).