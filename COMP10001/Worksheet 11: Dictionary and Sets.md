Worksheet 11: Dictionary and Sets
=================================

**Date:** March 27, 2024

**Subject:** COMP10001
Dictionaries:
-------------

*   Now let's talk about another very useful data type: dictionaries. The dict type allows you to create mappings from keys to values

*   For example, you might use a dictionary to map Australian state names to the names of their corresponding capital cities:
    ```python
        capitals = {'Victoria': 'Melbie',
            'New South Wales': 'Sydney',
            'Queensland': 'Brisbane',
            'Tasmania': 'Hobart',
            'South Australia': 'Adelaide',
            'Western Australia': 'Perth'}
        print(capitals['Tasmania'])
    ```

*   The keys in the above dictionary are strings which represent the names of the Australian states

*   Each key maps to a value, which also happens to be a string in this case

*   In the general case, the keys and values can be of different types

*   Dictionary values are constructed using the curly brace characters `{` and `}`.

*   As a special case, you can construct an empty dictionary using an opening and closing brace with nothing in between

*   Like lists and strings, dictionaries are indexable

*   However, the indices of dictionaries are keys of arbitrary value, whereas the indices of lists and strings are always integers

*   A given key can only occur once in the dictionary, and is associated with a unique value

*   You can look up values in a dictionary using the normal indexing notation. We call this performing a dictionary lookup:
```python
    capitals = {'Victoria': 'Melbie',
    'New South Wales': 'Sydney',
    'Queensland': 'Brisbane',
    'Tasmania': 'Hobart',
    'South Australia': 'Adelaide',
    'Western Australia': 'Perth'}
    print(capitals['Victoria'])
    print(capitals['Queensland'])
    print(capitals['ACT'])  # This is an ERROR!
```
```
    Melbie
    Brisbane
    Traceback (most recent call last):
    File "program.py", line 9, in <module>
    print(capitals['ACT'])
    KeyError: 'ACT'
```
*   The `.get()` method takes a key as an argument and returns the value associated with it. The difference between this and a direct lookup is that in the case a key doesn't exist, the lookup will throw an error while using `.get()` will simply return None.
    *   The dictionary name is before the dot and the key is inside the brackets

*   The `.pop()` method takes a key as an argument and returns the value, also deleting that key-value pair. This is similar to the way `.pop()` is used for lists in that it mutates the dictionary it is called over and returns the value if it executes successfully, or `KeyError` if the key wasn't found in the dictionary

*   The `.clear()` method deletes the entire contents of a dictionary. Like `.pop()`, this is a mutating method, so don't assign it to anything!

*   Dictionaries are mutable

*   So, like lists, their contents can be changed after they have been initialised. You can change the value which is associated with a key or add a new key-value pair to the dictionary using the assignment (`=`) operator:
    ```python
        capitals = {'Victoria': 'Melbie',
            'New South Wales': 'Sydney',
            'Queensland': 'Brisbane',
            'Tasmania': 'Hobart',
            'South Australia': 'Adelaide',
            'Western Australia': 'Perth'}
    
        print(capitals['Victoria'])
        
        capitals['Victoria'] = 'Melbourne'
        capitals['ACT'] = 'Canberra'
        
        print(capitals['Victoria'])
        print(capitals['ACT'])
    ```
    ```
        Melbie
        Melbourne
        Canberra
    ```
    
    *   `'Victoria'` now maps to the value `'Melbourne'` instead of `'Melbie'`, thus fixing the previous mistake. The key `'ACT'` was not present in the dictionary before the assignment statement, so the above code extends the dictionary with a new mapping entry.

*   You can test if a key is present in a dictionary using the `in` operator.

*   You can get the keys in a dictionary using the `.keys()` method.
    *   `.keys()` returns a special iterable collection called a `dict_keys` view object that supports iteration and the in operator like a list, but does not support indexing. If you want to index, you will have to convert it into a `list()` explicitly.

*   You can get the values in a dictionary (separate from the keys) using the `.values()` method. `.values()` returns a special iterable collection called a `dict_values` view object that acts much like the `dict_keys` object

*   Another useful method for dictionaries is the `.items()` method. Similar to `.keys()` and `.values()`, `.items()` returns a view object called `dict_items` which contains a 2-tuple for each `(key, value)` pair.

*   **Unpacking** allows you to assign the individual elements of an iterable to separate variables, and is helpful when iterating through a sequence made up of iterable elements of fixed length, such as a list (the sequence) of 3-letter strings (the iterable elements):
    ```python
        my_list = ["ABC", "DEF", "GHI"]
        for letter_0, letter_1, letter_2 in my_list:
        print(letter_2, letter_1, letter_0)
    ```
    ```
        C B A
        F E D
        I H G
    ```

*   The builtin `enumerate()` function is handy for taking advantage of unpacking. It takes a single iterable object and returns an **enumerate object** which can be iterated through to produce tuples containing elements together with their index.
    ```python
        my_list = ['elem1', 'elem2', 'elem3']
        
        my_enumerate = enumerate(my_list)
        
        for entry in my_enumerate:
        
            print(entry)
    ```
    ```
        `(0, 'elem1')`
        
        `(1, 'elem2')`
        
        `(2, 'elem3')`
    ```

*   The first element of each tuple is the index and the second is the element at that index. This can be useful if you need to retain a reference to the index of items as you iterate through them.

*   Unpacking with a `for` loop is a handy way of iterating through objects and their index at the same time:
    ```python
        my_tuple = ('first', 'second', 'third')
        
        for index, element in enumerate(my_tuple):
        
            print(index, element)
    ```
    ```
        0 first
        
        1 second
        
        2 third
    ```

*   Keys for dictionaries can only be immutable objects. That means you can use any of `int`, `float`, `str`, `tuple`, or `bool` as keys, but you cannot use `list`, or `set`

### Dictionary Summary:

We've learned about the `dict` data type and how it can be useful.

*   Dictionaries allow you to create mappings from keys to values. Keys and values can be of different types. There may only be one instance of a certain key in a dictionary, and it is associated with a unique value.

*   Keys must be immutable, but values can be of any type.

*   Dictionaries are especially good at counting things. This is a common use of them.

*   An empty dictionary is defined with an empty pair of curly braces `{}`.

*   A dictionary literal can initialise a dictionary with a number of key-value pairs, with the syntax `{<key1>: <value1>, <key2>: <value2>}`.

*   Dictionaries are mutable: you can change the value which is associated with a key or add a new key-value pair to a dictionary using the assignment (`=`) operator.
    ```python
        new_dict = {'number': 1, 'letter': 'a'}
        
        print(new_dict['number'])
        
        print(new_dict['hello'])  # KeyError
    ```

*   A **dictionary lookup** can be performed to return the value for a particular key, using familiar indexing notation: `<dict name>[<key>]`.

*   Attempting to look up a key which is not in the dictionary will result in a `KeyError`.

We learned about the following dictionary methods and operations:

*   The `.get()` method takes a key as an argument and returns the value associated with it, or `None` if the key doesn't exist.

*   The `.pop()` method takes a key as an argument and deletes the key-value pair, returning the value.

*   The `.clear()` method deletes all key-value pairs from the dictionary.

*   When used with a dictionary, the `in` operator will test for the presence of a key.

*   The `.keys()` and `.values()` methods return an iterable collection of the keys and values, respectively, of the dictionary they are called on.

*   The `.items()` method returns an iterable collection of tuples in the form `(key, value)` for every key-value entry in the dictionary.
    *   This tuple can be **unpacked** to separate the variables:
        ```python
            my_dict = {'first': 1, 'second': 2, 'third': 3}
            
            for key, value in my_dict.items():
            
                print(key, value)
        ```

Sets:
-----

*   Although a set with elements uses curly braces, you cannot use empty curly braces to define an empty set, as that is already used to define an empty dictionary. `set()` defines an empty set.

*   As there is no value associated with each key, we don't need to use the colon notation anymore, and it is this lack of colons (and keys) that allows Python to distinguish set literals from dictionaries.

*   The order of elements in a set is not significant (similar to dictionaries). But while dictionaries choose one arbitrary key ordering and stick with it (the order in which the keys were inserted), the ordering of sets is somewhat arbitrary, as you will see if you run the following code:

*   Because sets contain unique elements, they automatically remove duplicate elements

*   Like dictionary keys, sets may only contain **immutable** objects

*   Like lists, you can use the `in` operator with sets, to test for a given element

*   You can make sets from sequences. This is a good hack for removing duplicate elements

*   There are three useful operators which are unique to sets:
    
    *   **Union**: `set1 | set2` or `set1.union(set2)` returns a new set containing the items from `set1` combined with those from `set2`.
    
    *   **Intersection**: `set1 & set2` or `set1.intersection(set2)` returns a new set containing only items which are present in both `set1` and `set2`.
    
    *   **Difference**: `set1 - set2` or `set1.difference(set2)` returns a new set containing only items which are present in `set1` and not present in `set2` (that is: it removes elements in `set2` from `set1`).

*   Finally, as with lists, sets are **mutable**, so you can add and remove elements. Note `.add()` is the method to add an element to a set

*   You can also find the length of a set using `len()`

*   Sets and dictionaries are not sequences like lists, tuples, and strings

*   In fact, there is another category of types called **containers**. Containers are a data structure for storing other objects. Strings, lists, tuples, dictionaries, and sets are all containers. Sequences (lists, tuples and strings) are a subset of containers

*   All container types support the `in` operator: it makes sense that any type which can "contain" things can be asked whether it contains something.

*   Containers also generally support `len()` and iteration: dictionaries and sets both cycle through their elements in an arbitrary order.

*   Not all containers support indexing: only sequences do.

### Set Summary:

We've learned about the `set` data type and how it can be useful.

*   A set contains a series of unique values which have no concept of order. Sets may not be indexed.

*   Items in a set must be immutable.
    ```python
        empty_set = set()
        
        new_set = {1, 3, 3, 'hello'}
        
        print(new_set)  # duplicate 3 is deleted
        
        new_set.add(7)
        
        new_set.remove(3)
        
        print(new_set)
    ```

*   An empty set must be written as `set()`.

*   A set literal can be initialised with elements in a similar fashion to lists (by separating the elements with commas): `{<element1>, <element2>}`.

*   Sets are mutable: you can add a new element to a set with the `.add()` method, or remove an item with the `.remove()` method.

*   Duplicates of values already entered into a set are deleted, leaving just one of each value.

*   When used with a set, the `in` operator will test whether it contains a value.

*   Union (`|`), intersection (`&`), and difference () are three useful set operations.

*   Sets may not seem useful, but by adding items to them, performing set operations, querying membership, and perhaps converting to other types, they can be very handy in certain circumstances.

*   We also touched on **container types** which are types capable of storing collections of other objects. Lists, tuples, strings, dictionaries, and sets are all container types (with the first three also being sequences).
