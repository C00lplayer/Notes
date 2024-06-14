Worksheet 12: Advanced Functions
================================

**Date:** April 16, 2024

**Subject:** COMP10001

`None`:
-------

*   Returning none in a function is advantageous rather than to throw an error, as errors will cause the program to stop, suggesting that there's something wrong with the code that was written or the input.

*   If you'd like your code to handle the possibility of an empty list without causing a fuss, returning `None` is a good solution

*   Some functions don't need to have a `return` statement, and yet always have a return value

*   This is due to an implicit (bare) `return` statement at the end of every function, and the default value for `return` is `none`
    *   This also applies for when there are multiple paths through a function and execution doesn't reach a `return` for some input: `None` will be the default value returned in this case.

Multi-return Tuples:
--------------------

*   You can return multiple things from a function by listing the values separated by a comma in which python will return it as a multiple element tuple
    *   In this case the brackets are optional

**The Subtleties of Return:**
-----------------------------

*   When the code reaches a return statement it returns the value and aborts the running of the function entirely
    *   So anything after the return statement is redundant

### **None and return Summary:**

we've learned about the value `None`, using tuples to return multiple objects from a function and looked at some subtleties of `return`.

*   `None` is a unique value, of type `Nonetype`. There is no value of any other type which is equal to it.

*   `None` is especially good as a return value in the case of an empty input or if a value is needed to indicate the absence of some data.

*   `None` can be compared to using the `is` or `is not` operators.

*   Functions which have no `return` statement, will default to a return value of `None`.
    ```python
        print(None)
        
        print(type(None))
        
        print(None is None)
        
        print(False is not None)
    ```
    ```
        None
        <class 'NoneType'>
        True
        True
    ```

*   Tuples are a good choice when returning multiple values from a function, as they can contain as many objects as you like and fulfil `return`'s requirement that only one object may be returned.

*   When multiple objects separated by commas are written after `return`, Python will implicitly interpret them as a tuple, even if they are not surrounded by parentheses.
    ```python
        def my_func():
        
            return 1, 2, 3
        
        print(my_func())
    ```
    ```
        (1, 2, 3)
    ```

*   A `return` statement will terminate a function's execution, which can be useful for writing more efficient code, as in **lazy evaluation**.

Global and Local Namespaces:
----------------------------

*   Any variables defined in the function are created in a local namespace (accessible only within the local function call), and destroyed on return from the function

*   Whenever a function is called, it creates a local namespace in which to define its own variables, completely separate to the global namespace outside the function

*   When a variable is encountered in a function, Python first attempts to dereference it relative to the local namespace (of the current function call), and failing this, it attempts to dereference it relative to the global namespace
    *   This bypasses the local namespace of any other functions. In fact, the "local" namespace of a given function call is exactly that — local to that function call, and inaccessible from any other function call.

*   It is generally considered bad practice to reference global variables in functions, and notoriously hard to debug.

*   In fact, while Python allows you to implicitly dereference global variables in functions (i.e. use their values), if you attempt to assign a new value to a global variable within a function, all that will happen is that a local variable is created

### Summary

*   A namespace is a mapping of variable/function names to objects. It defines the collection of variables which can be used in a certain part of your program.

*   Any variables declared inside a function exist only in that function's local namespace. They are inaccessible from any other function call and are deleted when the function terminates.

*   When a variable of the same name exists in both the local and the global namespace, the local one is accessed when that variable name is used.

*   If a variable name is referenced in a function, Python will first attempt to dereference it relative to the local namespace, and failing that, will move to the global namespace. This means that it is possible to read a global variable from a local context, though it is not possible to change a global variable: an operation such as incrementing will cause an `UnboundLocalError` and assigning to a global variable will simply create a new local variable.

*   Global variables are appropriate for storing constant values (defined in ALLCAPS).

*   When a mutable object is passed into a local namespace, mutations made in the local space are reflected outside the function. This is due to call by object where one object is accessed via its (possibly many) variable name(s) as a reference, and changes made through one name are seen when accessed by any of its names.

Sort Keys and Lambda:
---------------------

*   A situation where it is useful that functions are objects is for a generic function which requires some specific behaviour to be specified for it to be run.

*   In this case, the function can take a function as an argument and use it inside the function body. This makes code modular and easy to extend.

*   An example of such a function is `map()` which takes two arguments: a function `func` and an iterable object. `map` applies `func` to every element in that iterable and returns an iterable **map object** (which can be converted to a list as below) containing all the return values in order. The function `func` could be anything
    ```python
        my_list = ['hello', 'WORLD', 'map']
        
        print(list(map(len, my_list)))
        
        print(list(map(str.isupper, my_list)))
    ```
    ```
        [5, 5, 3]
        
        [False, True, False]
    ```

*   In these examples we haven’t used brackets because we're not calling the functions (or methods). Rather, we're simply passing them as function objects to map(), where map can call them as and when it likes.

*   Another example is `filter()` which, like `map()`, takes a function and an iterable object. `filter` applies the function to each element of the iterable and stores those which return `True` in its output **map object**. This object can, again, be converted to a list to demonstrate how it filters out elements of the original iterable which return `False` for the given function:
    ```python
        my_list = ['hello', 'WORLD', 'filter!']
        
        print(list(filter(str.isalpha, my_list)))
        
        print(list(filter(str.isupper, my_list)))
    ```
    ```
        ['hello', 'WORLD']
        
        ['WORLD']
    ```
    
    *   The first application of `filter` above removes `'filter!'` from the output, since the exclamation mark is not an alphabetic character.
    
    *   The second function call removes any word which is not all-uppercase from the output, leaving `'WORLD'` as the only element output.

*   A function passed as `key` must take a single argument as input and return a value with which that argument should be sorted. `sorted()` will call the `key` function for every item in the list and sort them based on the return value which each item gives. Have a look at the example below:
    ```python
        def my_key(item):
        
            return item[2]        
        
        animals = ['kangaroo', 'tiger', 'elephant', 'giraffe']
        
        print(sorted(animals, key=my_key))
    ```
    ```
    
        ['elephant', 'tiger', 'kangaroo', 'giraffe']

    ```
    
    *   Because our `my_key()` function returns the `[2]` index of each item it's called over, the sort order of `'kangaroo'` is based on its third character `'n'`; for `'tiger'` it is `'g'`; for `'elephant'` it is `'e'`; and for `'giraffe'` it is `'r'`.
    
    *   Sorting these return values gives `('e', 'g', 'n', 'r')` which corresponds to (el**e**phant, ti**g**er, ka**n**garoo, gi**r**affe) as the order those animals are printed out in.

*   `lambda` is like a shortcut to `def` which defines a function for us in a single line of code. We call them _anonymous functions_ because they don't need names: they can be passed directly in contexts where a function is needed

*   Lambda is really only good for short, single line `return ...` style functions

*   Structure of `lambda`:
    ```python
        lambda <parameters>: <return value>
    ```
    
    *   It can have zero, one, or many parameters, separated by commas (without parentheses)
    
    *   The return value of the anonymous function is defined after the colon
    
    *   The whole `lambda` expression evaluates to this anonymous function, so it can be assigned to a function name or used once
    
    *   Examples:
        ```python
            func_none = lambda: 'Hello, world!'
            print(func_none())
            
            func_many = lambda a, b, c: a + b / c
            print(func_many(3, 5, 6))
        ```
        ```        
            Hello, world!
            3.8333333333333335
        ```

### **Sort keys and lambda Summary:**

We've learned how we can customise the way we sort data using `sorted`'s `key` argument, and how `lambda` can help us write `key` functions more efficiently.

*   Everything is Python is an object, and functions can be passed as an argument into other functions.

*   Passing functions into functions as arguments is useful for the `map()` and `filter()` functions.
    
    *   `map()` takes a function and an iterable object and applies the function to every element in the iterable object.
    
    *   `filter()` takes a function and an iterable object and keeps only elements of the iterable which return `True` when the function is applied to them.
    ```python
        words = ['lower', 'case', 'words.']
        
        print(list(map(str.upper, words)))
        
        print(list(filter(str.isalpha, words)))
    ```
    ```
    
        ['LOWER', 'CASE', 'WORDS.']
        
        ['lower', 'case']
    ```

*   We can define our own sort order by specifying `sorted()`'s `key` function. `sorted` will call this function with each item in the list it's sorting, and will use the return values to sort each object.

*   Using `def` to define each `key` function we need can be tedious and clutter our code, because `key` functions tend to be short and single-use.

*   `lambda` allows us to define **anonymous functions** inside a line of code. While they can be then assigned to an identifier if desired, they are most commonly used as single-use functions in defining a `key` function _in situ_ as part of our call to `sorted()` or `.sort()`.
    ```python
        words = ['lower', 'case', 'words']
        
        print(sorted(words, key=lambda x: x[::-1]))
    ```
    ```    
        ['case', 'lower', 'words']
    ```
