Worksheet 9: Mutability and Advanced Sequences
==============================================

**Date:** March 13, 2024

**Subject:** COMP10001

Mutability:
-----------

*   Tuples are immutable

*   An object is said to be mutable if its value (contents) can be changed after it is created.

*   If the value can't be changed, it is immutable.

*   If an object is mutable, then the object's value may change, while its id remains constant (as in, it stays the same object, only its value changes).

*   Usually when we perform operations we create a new object.

*   Integers are **immutable**.

*   There is a slight subtlety however, if we have a mutable object (like a list) within an immutable object (like a tuple we are allowed to change the value of the mutable object.
    *   Note that the ids of the objects in the tuple do not change, which means the "value" of the tuple is not changing, which is why the change is allowed

*   It is important to understand that the assignment operator (=) points a variable to a particular object:
    *   If we point two variables to the same mutable object and change one of them, we will see the change reflected in the other one too since they are both pointing to the same object!

>[!Tip]
>**The** **`is`** **operator:**
> *   You can use the `is` operator to see whether two variables point to the same object. Unlike `==`, which will return True if the two objects are equal in value, `is` checks that the objects have an identical id as well.
>```python
>list1 = [5]
>list2 = list1
>list3 = [5]
>print("id of list1:", id(list1))
>print("id of list2:", id(list2))
>print("id of list3:", id(list3))
>print("list1 is list2:", list1 is list2)
>print("list1 == list3:", list1 == list3)
>print("list1 is list3:", list1 is list3)
>```
>```
>id of list1: 4140172364
>id of list2: 4140172364
>id of list3: 4140172492
>list1 is list2: True
>list1 == list3: True
>list1 is list3: False
>```
>*   Since `list1` and `list2` point to the same object, `is` returns `True`.
>*   `list1` and `list3` have contents which are equal (the integer 5) but they are different objects with different ids, so return `True` for `==` and `False` for the is comparison.

### Mutability Summary:

We have learned about mutability and the effects of mutating an object.

*   An object is **mutable** if its value (contents) can be changed after it is created. If the value can't be changed, it is **immutable**.

*   An object's type dictates whether it is mutable or not. Lists are the only type we have seen so far which is mutable. Strings, tuples, integers, floats and booleans are immutable.

*   An object's `id` is its unique identifier. Mutable objects may change their value while keeping the same id.

*   A `TypeError` will result when attempting to mutate an immutable object.

*   Incrementing a variable (using += for instance) is equivalent to reassigning the variable name with a new number and is not an instance of mutation.

*   Objects inside a tuple (which is immutable) may be mutated since an object's `id` doesn't change when it is mutated.

*   The assignment operator points an identifier towards an object. It is therefore possible that the same object can be pointed to by many different variable names. Hence in the case of mutability, editing an object via one variable name will change its value for every variable name pointing at it.

*   If a function mutates one of its arguments, the change will be reflected outside of the function.

Advanced Lists:
---------------

*   Python provides a number of useful methods for manipulating lists.

*   The `.append(object)` method adds `object` onto the end of the list it is called on:
    ```python
        chomsky = ['colourless', 'green', 'ideas']
        chomsky.append('sleep')
        print(chomsky)
    ```
    ```
        ['colourless', 'green', 'ideas', 'sleep']
    ```

*   `.pop()` removes the final element from the (non-empty) list it is called on. If called with an integer argument `.pop(index)` removes the element at the specified index.

*   `.pop()` mutates the list to remove the desired element, though it returns that element as its return value so that you can check it's what you were expecting.

*   `.insert(index, object)` adds object into the list it is called on at the specific index given (remember that indices start at zero):
```python
    chomsky = ['colourless', 'green', 'ideas']
    chomsky.insert(1, 'sleep')
    print(chomsky)
```
```
    ['colourless', 'sleep', 'green', 'ideas']
```
*   `.copy()` returns a new list with the same contents as the list it is called on.
    *   This new list has a different id than the original one, so either list can be mutated without affecting the other one.

*   `.remove(value)` deletes the first occurrence of an object equalling value from the list it is called on.
    *   A ValueError occurs if there is no such item in the list.

*   And finally, `.index(value)` is a non-mutating method which returns the index of, again, the first occurrence of value in a list, as seen in the following example, where the list contains multiple instances of 'ideas'.
    *   A `ValueError` occurs if the argument to `.index()` is not in the list:

*   The `.split()` method. It is a convenient way of turning a string into a list of words.
    
    *   By default, .split() segments a string into a list of substrings based on "whitespace" separators (space characters, tab characters, and line breaks), removing the separators in the process.
    
    *   It is possible to change this behaviour by specifying a separator in the argument to .split():
        ```python
            print("1,2,3".split(","))
            print("l00k b4 U l3ap".split("b4"))
        ```
        ```
            ['1', '2', '3']
            ['l00k ', ' U l3ap']
        ```

*   The `.join()` method takes an iterable object containing strings as input and joins those strings together into one:
```python
    print(''.join(['j', 'o', 'i', 'n', 'e', 'd']))
```
```
    joined
```
*   `.join()` is a method which is called on a string. In the above example, this string was an empty string - have a guess at what it does. It is a separator string which is inserted between the strings in the list when they are joined. It is like the argument which is given to split.
    ```python
        joined = ' and '.join(['apple', 'carrot', 'tomato'])
        print('I like', joined)
    ```
    ```
        I like apple and carrot and tomato
    ```

*   You can compare splitting and joining by how they are called below:
    ```python
        list = string.split(sep)  # string -> list
        string = sep.join(list)  # list -> string
    ```

*   One list operation that you will find many applications for is sorting the elements

*   There are two ways of doing this, which you will inevitably confuse at some point because of the names being so similar:
    
    1.  The `sorted()` function
    
    2.  The `.sort()` method

*   `sorted()` takes a list as an argument and returns a new list with the elements in sorted order (without mutating the original list).
    *   For example:
        ```python
            randlist = [4, 1, 3.0, 2, 5]
            print(sorted(randlist))
            print(randlist)
        ```
        ```
            [1, 2, 3.0, 4, 5]
            [4, 1, 3.0, 2, 5]
        ```

*   It can also be applied to a list of strings, in which case the sort order is based on the underlying Unicode ord() values:
    ```python
        print(sorted(['abacus', 'a', 'aardvark', 'ABC']))
    ```
    ```
        ['ABC', 'a', 'aardvark', 'abacus']
    ```
*   If you wish to reverse-sort the list, simply set the optional reverse keyword argument to True:
    ```python
        randlist = [4, 1, 3.0, 2, 5]
        print(sorted(randlist, reverse=True))
        print(randlist)
    ```
    ```
        [5, 4, 3.0, 2, 1]
        [4, 1, 3.0, 2, 5]
    ```

*   The `.sort() method`, which operates in-place, in that it mutates the list so that the elements are sorted (i.e. the original ordering of elements is potentially changed):
    ```python
        randlist = [4, 1, 3.0, 2, 5]
        randlist.sort()
        print(randlist)
    ```
    ```
        [1, 2, 3.0, 4, 5]
    ```

*   The confusion comes with the subtly different way which sorted() and .sort() should be written in code. sorted() returns its result, so should be called and assigned like this:
    ```python
        randlist = [4, 1, 3.0, 2, 5]
        randlist = sorted(randlist)
    ```

*   However, since .sort() mutates the list, it doesn't return anything and should definitely not be assigned:
    ```python
        randlist = [4, 1, 3.0, 2, 5]
        randlist.sort()
    ```

*   Another advantage of sorted() is that it can be applied to any sequence, including lists and tuples (although it will always return a list):
    ```python
        print(sorted("bananas"))
        print(sorted((3, 1, 5)))
    ```
    ```
        ['a', 'a', 'a', 'b', 'n', 'n', 's']
        [1, 3, 5]
    ```

*   `sorted()` and `.sort()` work by ordering a list with elements from smallest to largest, but what if there are identical elements

*   The first thing `sorted()` does is order elements based on the first index of them. This would be the first character in a string, or the first item if sorting a series of lists or tuples. In a list of numbers, there's only one thing to sort with: the number!
    *   If there are ties, such as two strings with the same first letter, the second letter is used, as we see below:
        ```python
            strings = ['ap', 'r', 'ab', 'rh', 'rz', 'a', 'rc', 'cg']
            print(sorted(strings))
        ```
        ```
            ['a', 'ab', 'ap', 'cg', 'r', 'rc', 'rh', 'rz']
        ```

*   Tiebreaking can be even more interesting when sorting tuples or lists, in which the second element of each tuple can be used as a tiebreaker for the first:
    ```python
        tuples = [(1, 'hi'), (4, 'bye'), (4, 'hi'), (1, 'ace')]
        print(sorted(tuples))
    ```
    ```
        [(1, 'ace'), (1, 'hi'), (4, 'bye'), (4, 'hi')]
    ```

### List Methods Summary:

We have seen some useful list methods and looked at sorting. These were the methods we introduced:

*   The `.append(object)` method adds object onto the end of the list it is called on.

*   `.pop()` removes the final element from the (non-empty) list it is called on. If called with an integer argument `.pop(index)` removes the element at the specified index.

*   `.insert(index, object)` adds object into the list it is called on at the specific index given (remember that indices start at zero).

*   `.copy()` returns a new list with the same contents as, but a different id than, the list it is called on.

*   `.remove(value)` deletes the first occurrence of an object equalling value from the list it is called on.

*   `.index(value)` is a non-mutating method which returns the index of the first occurrence of value in the list it is called on.

We gave a few warnings about the above methods:

*   A `ValueError` occurs if the item being searched for by `.remove()` or `.index()` doesn't exist.

*   Since `.index()` and `.remove()` match the first instance of a value in a list, it is best to avoid them unless you are sure the first instance is what you want.

*   Be careful not to mutate lists when iterating over them, as this can cause effects which are unexpected and hard to debug.

*   The `.split()` method divides a string into a list of substrings based on the location of whitespace.

*   The `.join()` method joins a list of strings together into one string.

We had a brief look at `zip()`, which takes multiple iterable objects and groups together elements at corresponding indices of those inputs.

We introduced sorting:

*   The `sorted()` function will return a sorted copy of the list entered as an argument. The `.sort()` method will mutate the list it is called on to sort it, returning None.

*   Setting the keyword argument `reverse=True` to either `sorted()` or `.sort()` will reverse the sort order.

*   Trying to assign the value of a mutating method such as `.sort()` will cause trouble since it returns `None` and is not intended to be assigned. It's safer to stick to `sorted()` unless you're sure you would like to use the mutating `.sort()`.

*   Tiebreaking works in a similar way to dictionary sorting: the first character/item is looked at first, then the next if the first are identical, and so on.
