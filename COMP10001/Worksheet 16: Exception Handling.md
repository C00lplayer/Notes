Worksheet 16: **Exception Handling**
====================================

**Date:** April 29, 2024

**Subject:** COMP10001


**Why Use Exceptions:**
-----------------------

*   As we have seen in previous worksheets, it's important to write code that behaves robustly, predictably, and elegantly when encountering unexpected input, whether this is input from a user or an argument provided to a call to a function.

*   This means that rather than letting the program crash when an unexpected error occurs, the program handles the errors by either preventing the error from occurring to begin with, or by explicitly handling the error in some way, so that the program can continue operating normally

*   The call to `divide(3, 0)` fails, because mathematically we cannot [divide a number by zero](https://en.wikipedia.org/wiki/Division_by_zero). However, as this **exceptional case** is not handled by the program, **the program crashes with an exception**

*   Using **exceptions** are a way of indicating that an "exceptional case" has occurred, while not handling the case immediately.

*   When you **raise** an exception, an exception object is created, which is passed up the call-stack to the caller of the function to handle.

*   You can raise an exception by writing `raise`, the name of the exception type you want to raise (more on this later), and an error message you want to pass along in the error object.
    ```python
        raise Exception('An error has occurred!')
    ```

*   This is only half of the story, however: while we've indicated that we've detected an erroneous input of a particular type, we don't yet have a way of handling the error, resulting in the program crashing.

*   We can write code to **handle the exception**, allowing the program to do something about the problem, and carry on [doing its thing](https://giphy.com/gifs/lifetimetelly-lifetime-who-cares-judge-judy-3oz8xTLGJ6z4pfipVe/fullscreen). Python provides the `try ... except` construct to catch and deal with exceptions. The basic syntax is:
```python
    try:
        # Code that may raise an exception
    except <SomeExceptionType> as <some_variable_name>:
        # The Exception Handler.
        # What to do if a matching exception is raised.
```
*   The code in the `except` block will run if an exception occurs that matches the type of exception indicated by the `except` block.

*   The exception object will be assigned to the variable name `<some_variable_name>`, which will allow you do things like retrieve the error message from the exception and print it

**Exception Handling:**
-----------------------

*   There are many built-in exceptions in Python:

|**Exception**|**Description**|
|-------------|---------------|
|`IndexError`|Raised when a sequence index is out of range, e.g. `[][0]`.|
|`ZeroDivisionError`|Raised when the second argument of a division or modulo operation is zero, e.g. `1/0`.|
|`TypeError`|Raised when an operation or function is applied to an inappropriate type, e.g. `'e'+3`|
|`NameError`|Raised when you try to reference a variable which hasn't been assigned, e.g. `num`.|
|`KeyError`|Raised when a key does not exist in the dictionary, e.g. `{}['a']`.|

*   We can work with specific exceptions the same way we would work with the general `Exception`.
    *   For example, we could raise an `IndexError` simply by using `IndexError()` as we would have with `Exception()`.
        ```python
            raise IndexError('An index error occurred!!')
        ```

*   Back to our previous running example, if we were to rely on the built-in `ZeroDivisionError` exception, then we could catch it as follows:
```python
    def divide(numerator, denominator):
      # We don't do anything here to try and detect the error
      # that is about to occur, but rather let Python throw a
      # built-in exception if the error occurs.
      return numerator / denominator
    numerator = int(input('Enter a numerator: '))
    result = None
    while result is None:
      denominator = int(input('Enter a denominator: '))
      try:
        result = divide(numerator, denominator)
      except ZeroDivisionError as e:
        # We write an error handler for the ZeroDivisionError here.
        print(f'{e}\nPlease enter a non-zero denominator.')
    print(f'Result is {result}')
```
*   When working with exceptions, it's possible that more than one type of exception could occur in any piece of code. In such a case, you may wish the code to do something different to handle each exception
    
    *   For example, we might want to write a program that allows the user to retrieve a value from a list, by providing an index number. In such a case, we run the risk that the user enters an index that is out of range, resulting in an `IndexError`.
    
    *   At the same time, it's also possible that the user enters a value which is not an integer, resulting in a `ValueError` when trying to convert the input string to an integer.
    
    *   We could write code that handles both exceptions, as follows:
```python
    animals = ["sheep", "cow"]
    # Keep asking for input until we successfully read an input in.
    while True:
        try:
            index = int(input('Enter an index: '))
            print(f'The animal is a {animals[index]}')
            # We successfully read some input, break out of the loop here.
            break
        except IndexError:
            print(f'Out of range! Enter a number in the range 0 to {len(animals) - 1} or {-len(animals)} to -1.')
        except ValueError:
            print('Please enter an integer.')
```
*   Exceptions are checked in the sequence provided — that is to say, the order of exceptions can matter

*   This matters particularly if you intend to use the general `Exception()` to raise your own exceptions, but at the same time also handle Python's built-in exceptions

*   This is because when capturing exceptions, catching the general `Exception` will mean capturing all exceptions, rather than a specific exception

*   Python also implements an `else` clause, to be optionally added after the `except` blocks. The `else` block is executed if no exception was raised

*   This is useful as rather than putting all the code you want to run in the `try` block, you can focus on only the code you want to handle errors in, and put the remainder of the code in the `else` block.
    *   This prevents accidental catching of errors that could occur in other parts of code that you did not intend to handle, and makes it clearer exactly what code you are handling with your `try ... except` blocks.

*   Last of all, there is the `finally` clause, which goes after everything.
    *   It is run when exiting the `try` statement. This means even if you have a  `return`  or  `break`  statement within a `try ... except` construct, the code in the `finally` block will run

*   The `finally` block will also always run regardless of whether an exception occurred or not, which is why it is especially useful for releasing resources or performing cleanup operations, such as the closing of files.

*   There is a built-in function in Python to make sure that certain conditions are met: the `assert(condition)` function throws an `AssertionError` if the Boolean condition specified in its argument is _not_ met (and silently succeeds if the condition _is_ met)
    *   This condition is generally a test for validity of input, or confirmation that an action which the program depends on has successfully completed.

*   `assert()` can be useful for proactively picking up on errant inputs; for example if someone uses a module you wrote incorrectly, they would see the error. Here is an example of a program that uses `assert()`. Try calling the function with a negative value.
    ```python
        from math import sqrt
        def sqrt(val):
            assert(val > 0)
            return sqrt(val)
        print(sqrt(-1))
    ```
