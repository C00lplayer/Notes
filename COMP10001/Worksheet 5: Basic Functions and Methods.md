Worksheet 5: Basic Functions and Methods
========================================

**Date:** March 13, 2024

**Subject:** COMP10001

Introduction to Functions:
--------------------------

*   Suppose we have the following formula for the number of standard drinks in a drink: `std_drinks = volume * percentage * 0.789`
    
    *   Here volume is a variable (the size of your drink in litres), and percentage is the percentage of alcohol

*   To calculate the number of standard drinks with a variable volume and alcohol percentage is done in the form of a user-defined function:
``` python
    def std_drinks(volume, percentage):
      return volume * percentage * 0.789
  ```
*   In this example the function name is `std_drinks`

*   `Volume` and `percentage` are called **parameters**
    
    *   They take the values you provide when you **call** (i.e. use) the function.
    
    *   The values themselves are called **arguments**

*   The function is called by placing a pair of brackets () after the function name, and putting the arguments inside them.

*   The expression after `return` is what the function will output.
    *   This means that when we write the expression `std_drinks(0.375, 13.5)` in our code, it **evaluates** to the `return` value of the function, ready to be assigned to a variable or `print`ed out

Defining Functions:
-------------------

*   The basic components of a function are:
    
    1.  The function name;
    
    2.  The parameters;
    
    3.  The body, where the actual computation associated with the function occurs;
    
    4.  Some mechanism for returning a value and exiting the function.

*   First, to define our function we use the keyword def, followed by whitespace, the function name, a set of parentheses, and a colon (:)
    *   For example: `def my_first_function():`

*   Second, we insert the parameters within the parentheses in the function definition, separated by commas:
    *   For example: `def my_first_function(num0, num1, num2):`

*   The third thing we do in a function definition is to associate the code that will be executed each time the function is called, in the form of a block, whitespace-indented from the function header
    *   In the same way that we associated a block of code with an if, elif or else statement

*   The fourth critical component: a way of defining what is the result of a function. This is done with the return statement, which takes a single value

*   Putting all this together we get:
```python
    def my_first_function(num0, num1, num2):
        maxnum = num0
        if num1 > maxnum:
            maxnum = num1
        if num2 > maxnum:
            maxnum = num2
        return maxnum
```
*   It is important to recognise that earlier we were using print() to see output on the screen. Functions (other than `print()`) do not display any output unless that output is explicitly printed

*   Now you can call your function but you must follow some rules:
    
    1.  Only after defining your function can you call your function
    
    2.  Each time you call the function, it is evaluated with the provided arguments, if you call it again with a different argument, the two different calls have no connection to each other: Python will not remember the argument values of previous function calls in subsequent ones.

>[!Caution]
>When the `return` statement is executed in a function, the function stops immediately, and `returns` the value given. This means that anything in your function after the `return` statement will not be executed

### Functions Summary:

*   We have formally introduced functions and stepped through how we can define our own.

*   A function takes input, processes some task and returns an output.

*   Functions allow for a block of code to be run without needing to write it out each time. This contributes to cleaner code and more logical organisation of functionality.

*   A function is used (called) by writing its name followed by a pair of brackets (). Input arguments (if any) are written inside the brackets, separated by commas. The function's return value (if any) is what the function call will evaluate to and can then be assigned to a variable or printed or anything else.

*   This is the structure of a function definition:
```python
    def <function name>(<parameter1>, <parameter2>):
    <block of code>
```
*   The components are:
    
    1.  The function name
        
        *   This is given after the def keyword.
        
        *   The rules for valid function names are the same as those for valid variable names.
    
    2.  The parameters
    
    *   These are given inside the brackets, separated by commas. There can be as many as you like, or none.
    
    3.  The function body:
    
    *   This is given as a block of code after the def line, indented by a recommended four spaces.
    
    4.  A mechanism for returning a result from the function
    
    *   This is given by the return statement, where the value after the return keyword becomes the result which the function evaluates to when it is called.
    
    *   Upon reaching a return statement, the function terminates. If no statement is reached, the function executes until the end.
    
    *   If there are multiple return statements, only the first one which is executed will have effect: at this point the function terminates.

More on Functions:
------------------

*   To define functions with more than 1 parameter we have multiple comma-separated arguments, as per our original description of a function. There are a number of things to note here:
1.  The parameters must have different names, in order to be able to tell them apart, e.g. see what happens when you try to evaluate the following function definition:
```python
    def function(a, a, a):
    return a
```
2.  By default, the ordering of the arguments in the function call will determine which function argument is set to what value:
```python
    def swapped_sum(a, b):
        return b+a
    print(swapped_sum("a", "b"))
    print(swapped_sum("b", "c"))
```
3.  Just like it is possible for a function to have no return value, it is possible to have a function with no parameters. In this case the function definition will have empty parentheses, and any function calls will similarly have empty parentheses, e.g.:
```python
    def error_code():
        return -1
    print(error_code())
```
*   A default argument is an argument value which is assigned to a function parameter to act as that parameter's default value in the case that one is not given when the function is called

>[!Tip]
>The `print()` function has a couple of parameters with default arguments: `sep` and `end`.
>`sep` is a string which is placed between each separate value being printed.
>`sep`'s default argument is a space. `end` is a string which is placed at the end of the output, defaulting to a character `'\n'` which specifies that there should be a new line.

*   **Methods** are special functions that belong to specific data types.
    *   An example of a method is the `.upper()` method, which is specific to the `str` type, and returns the string it was called from, converted to uppercase

*   Methods are called **on** some data

*   Just as was the case with functions, method calls always require parentheses, and if there are no arguments, the brackets should be empty

*   There are lots and lots of methods for each type. You can use the `dir()` function to find their names. You can think of it as a **directory** of everything related to the thing you give it, which could be a value or a type.

*   The `help()` function can also be useful. It prints out information about how to use whatever you pass it. Sometimes it can be heavy handed on technical information though, so don't hesitate to search online

### More Functions Summary:

We have made a few extra notes about functions, and introduced methods.

When a function has multiple parameters:

*   Each one must have a different name.

*   The order of the parameters in the function definition must be the same as that of the arguments when calling the function (unless keywords are used).

*   It may be convenient to call the function using parameter names as keywords to match parameters to their values. This means they can be written in any order. Once one argument is given with a keyword, all subsequent arguments must also be given with keywords.
```python
    def my_func(param1, param2, param3):
    print(param1, param2, param3)
    my_func("hello", param3="function", param2="there,")
```
*   A function may have no parameters, but (empty) brackets are still required when calling it.

*   An argument may be given a default value in the function definition with keyword assignment syntax. If that argument is not specified when the function is called, the default value is used.
```python
    def my_func(param="default arg"):
    print(param)
    my_func()
```
*   Methods are functions which are tied to a data type. They are called on an object by putting a dot between the object's name and the method call.

*   Except for how methods are called with the dot notation, they work in the same way as functions, taking input arguments in parentheses and returning an output.

*   The dir() function can be used to find the name of all methods associated with an object.
