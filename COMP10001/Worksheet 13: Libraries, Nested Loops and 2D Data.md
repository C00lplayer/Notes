Worksheet 13: ****Libraries, Nested Loops and 2D Data****
=========================================================

**Date:** April 23, 2024

**Subject:** COMP10001

Libraries:
----------

*   A **library** is a collection of functions and constants that relate to a particular style of analysis.
    *   For example, there is a library for basic mathematical and statistical functions, another library for advanced iterators, and a different library again for advanced data structures used for storage purposes.

*   Note that libraries are also sometimes called **modules**

*   Libraries which are part of the default Python distribution are called **standard libraries**

*   To gain access to the functions within a given library, you must first tell Python to enable it, using the `import` statement, followed by a space and the name of the library, e.g., in the case of the `math` library:
    ```python
        import math
    ```
*   The `math` library provides many mathematical functions such as `.sqrt()` (to calculate the square root of a number), `.log10()` (to calculate the base-10 logarithm of a number), and `.factorial()` (to calculate the factorial of a number

*   The `math` library also supplies some important mathematical constants in the form of numeric variables, notably π and e. These are the closest `float` numbers to the actual values (since they are infinite it would be impossible to store them as an object precisely).

*   One downside to the standard `import` method is that, if the library has a long-winded name, it can be odious to have to type the full library name every time you want to use it. Python supports the importing of libraries under pseudonyms via an expanded `import` statement:
    ```python
        import <library> as <name>
    ```

*   This will import the `<library>` assigning it to an identifier `<name>` of our choosing.
    ```python
        import math as m
        
        print(m.pi)
        
        print(m.sqrt(2))
    ```

*   Alternatively, it is possible to selectively import objects in a given library into the local namespace of a program, to be accessed directly as functions and variables, using
    ```python
        from <library> import <objects>
    ```

*   Where you can list multiple objects to import, separated by commas.
    ```python
        from math import pi, sqrt
        
        print(pi)
        
        print(sqrt(2))
        
        print(e)
    ```

*   You can even use the `as` keyword from above to name each of the objects imported. This isn't much help here though: `pi` and `sqrt` are already very short names!
    ```python
        from math import pi as my_pi, sqrt as my_sqrt
        
        print(my_pi)
        
        print(my_sqrt(2))
    ```

*   As a final option, it is possible to import _all_ objects in a given library into the local namespace of a program, using `*`, e.g.:
    ```python
        from math import *
        
        print(pi)
        
        print(sqrt(2))
        
        print(e)
    ```

*   In terms of style, `import` statements should always be at the start of your program, before everything else

**Default Dictionaries:**
-------------------------

*   The **default dictionary** provides a shortcut when finding frequencies

*   It is a _very_ useful data type which you can import from the standard library `collections`. Default dictionaries are like regular dictionaries, but if you request a key which is not in the dictionary, rather than raise a `KeyError`, a default dictionary will do two things:
    
    *   It creates a default value for the key and returns it.
    
    *   It adds the `{key: value}` pair to the dictionary for future reference.

*   The default dictionary lives in the `collections` library and is named `defaultdict`. To use a defaultdict in your code, you need to import it with this or a similar `import` variant:
    ```python
        from collections import defaultdict
    ```

*   To create a new `defaultdict` object, we need to specify which **data type** the default values of the dictionary should be. When the defaultdict encounters a key it hasn't seen before, it will assign that key a default value which is the "zero value" of that type, or an empty container for container types.
    
    *   That means for `list`, new keys will be initialised to the empty list `[]`; for `str`, the empty string `""`; for `int`, `0`; for `float`, `0.0`; and so on
    
    *   e.g:
        ```python
            my_dict = defaultdict(<type>)
        ```

### Libraries and defaultdict Summary:

We've learned about libraries and default dictionaries.

*   A **library** is a collection of functions and constants which extend Python's capabilities to perform more diverse operations.

*   Libraries may be imported by running `import <library>`. Specific methods or variables may be imported with from `<library> import <objects>`.

*   Import statements should be written at the very top of a program.
    ```python
        from math import sqrt, pi
        print(sqrt(9))
        print(pi)
    ```
    ```
        3.0
        3.141592653589793
    ```

*   Standard libraries are those which are included in the standard Python distribution.

*   `math` standard library contains many mathematical functions and constants, such as the `sqrt`() function and the value of `pi`.
    ```python
        from collections import defaultdict
        my_dict = defaultdict(float)
        print(my_dict['a key'])
        print(my_dict)
    ```
    ```
        0.0
        defaultdict(<class 'float'>, {'a key': 0.0})
    ```
*   A **default dictionary** is a useful data type contained inside the collections library.

*   Default dictionaries are useful because, when queried with a key which is not yet in the dictionary, rather than raising a `KeyError`, the default dictionary adds it as a new entry, with its value set to a default value.

*   To create a new defaultdict, a type must be given as an argument. This dictates which default value will be initialised for keys which are not yet in the dictionary.

*   The default value is the "zero-value" of each type, which is 0 for numbers and an empty container for container types.

*   A default dictionary is like a regular dictionary wrapped in the default structure, which remembers the data type of default values. Defaultdicts can perform all operations regular dictionaries can. Importantly, values are not constrained to the default type (and indeed, the default type is only used to create a value when a KeyError would otherwise have arisen).

2D Data
-------

*   A lot of data, such as images or tables, is stored in **two-dimensional** form consisting of rows and columns. You require two indices to access the elements of two-dimensional data: the first index refers to the row number and the second index refers to the column number.

### **Nested Loops and 2D Data Summary:**

Over the last few slides, we've learned about nested loops and two-dimensional data.

*   A loop placed inside another loop is called a **nested loop**.

*   Nested loops contain an **inner** and an **outer** loop. The inner loop is contained inside the outer loop's body.

*   `break` terminates only the single loop it is contained in. If it is executed in an inner loop, the outer loop will continue running.
    ```python
        for outer in 'loop':
        
            for inner in 'loop':
        
                if inner == 'o' and outer == 'o':
        
                    break
        
                print(outer, inner)
    ```
    ```
        l l
        l o
        l o
        l p
        o l
        o l
        p l
        p o
        p o
        p p
    ```

*   **Linear** (or one-dimensional) data contains a single item stored at each index.

*   **Two-dimensional** data contains rows and columns, so at each index there is another series of data to be looked through.

*   Two-dimensional data can be stored in Python as a **nested** list, and could then be accessed using **nested** loops.

*   Image data (a `list` of `list`s of pixels) is an example of two-dimensional data.
    ```python
        row1 = ['linear', 'data']
        
        row2 = [5, 2]
        
        row3 = [4, 7]
        
        two_dim_data = [row1, row2, row3]
        
        for row in two_dim_data:
        
            for value in row:
        
                print(value, end=" ")
        
            print()
    ```
    ```
        linear data 
        
        5 2 
        
        4 7
    ```
