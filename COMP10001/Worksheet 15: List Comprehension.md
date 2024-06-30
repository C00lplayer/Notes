Worksheet 15: List Comprehension
================================

**Date:** April 29, 2024

**Subject:** COMP10001


List Comprehension:
-------------------

*   Initially we have been constructing lists using `for` loops, first initialising the list outside the `for` loop, then iterating over some sequence and using `.append()` or list concatenation to incrementally add elements to the list. 

*   **List comprehensions** are a really nice shortcut to construct lists in one line.

*   Suppose we want to square all the elements of a list of numbers.
    
    *   Using a `for` loop, we would do this as follows:
        ```python
            lst = [1, 4, 3, 5, 2]
            lst2 = []
            for x in lst:
                lst2.append(x**2)
        ```
    
    *   But with a list comprehension, we can perform exactly the same operation as follows:
        ```python
            lst = [1, 4, 3, 5, 2]
            lst2 = [x**2 for x in lst]
        ```

*   We can also use it to filter elements of one list based on a simple condition. Below we create a list of only the elements of the old list which are multiples of three:
    ```python
        lst = [1, 4, 3, 5, 2, 4, 8, 10, 9]
        lst2 = [y for y in lst if y % 3 == 0]
    ```

*   The general form of a list comprehension is as follows:
    ```python
        [<expr> for var in old_list <optional condition>]
    ```

*   You can also use the same syntax to declare a **dictionary** comprehension and a **set** comprehension.
    ```python
        my_word = 'guitar'
        my_dict = {letter: i for i, letter in enumerate(my_word)
    ```
    *   The trusty `enumerate()` function generates a tuple with each element's index.
    
    *   Note that the above code will only work properly if all characters in the word are unique as the key’s in a dictionary are unique

*   If you want to add more than 1 condition use the following structure:
    ```python
        [<expr> if <condition> else
                        <expr> if <condition> else
                        <expr> if <condition> else
                        <expr> for <var> in >iterable>]
    ```

### List Comprehension Summary:

We have learned how list comprehensions are a handy shortcut for generating lists.

*   Below is the general structure of a list comprehension, with its translation without using a comprehension:
    ```python
        new_list = [<expr> for var in old_list <optional condition>]
    ```

    ```python
        new_list = []
        
        for var in old_list:
        
            <optional condition>
        
                new_list.append(<expr>)
    ```

*   A new list is created containing `<expr>` which is evaluated for each iteration of the `for` loop.

*   An optional condition can be included as a filter, controlling whether each value is or is not added to the list.

*   List comprehensions are useful in many situations, especially when initialising new lists with a certain structure

Iterators:
----------

*   Simplistically, an iterator is an object for iterating over other objects, like lists or strings. The iterator object keeps track of where it is up to in the object, implements a method that returns the next element, and generates an error when it gets to the end ("throws an exception")

*   You can make an iterator object out of all the sequences you have seen by calling the `iter()` function, and iterate once over the iterator object by calling the `next()` function (as we saw with the `csv` library).

*   Below we make an iterator out of a `list` and call the `next()` function a couple of times:
```python
    list1 = [1, 5]
    my_iterator = iter(list1)
    print(next(my_iterator))
    print(next(my_iterator))
    
    # This will generate an error because we have reached the end.
    print(next(my_iterator))
```
*   We have been using iterators implicitly. The `for ... in` loop works by calling the  `iter()`  function to make an iterable out of whatever we are iterating over, then calling `next()` behind the scenes.

*   It is important to remember that iterators keep track of where they are up to, and every time `next()` is called, move "forward", **but there is no way to move backward**

*   This means we have to be careful when using constructs such as `for` which implicitly reference `next()` as we cannot call it again

*   Iterators are similar to sequences, but differ in some important ways, as summarised below:

|Sequences|Iterators|
|---------|---------|
|Have random access (you can access any element in the sequence, as many times as you like)|No random access|
|No position tracking within the sequence|Remembers where you are up to|
|You can use `len()` to calculate the length|Cannot use `len()`|
|Must be finite|Can be infinite|
|You can traverse it many times|You can only traverse it once, forwards|


### Iterators Summary:

Over the last few slides, we've learned about iterators and how we can use them.

*   An **iterator** is an object which may be iterated through.

*   Iterators can be created from any **iterable** object using the `iter()` function. `next()` is used to step from one object to the next. A `StopIteration` exception will be raised when the iterator runs out of objects to iterate over.

*   Iterators are efficient because the whole sequence of objects doesn't need to be stored in memory: elements are accessed one at a time.

*   Iterators are similar to sequences, but important differences are: they operate in a strictly sequential manner, cannot step backwards, and can be infinite.

In a small aside, we also considered how all container objects are iterables and noted that some standard functions such as `sum()` take any iterable, not just lists\\

**Itertools:**
--------------

*   One of many modules that uses iterator objects is the `itertools` library

*   The first method we introduce will allow us to generate **permutations** of a group of objects
    
    *   A permutation of a group of objects is a particular ordering of a sub-grouping of its objects.
        
        *   For example, the letters ABC can be arranged in 6 ways: ABC, ACB, BAC, BCA, CAB, and CBA.
        
        *   We say there are 6 possible permutations of length 3.
    
    *   We can also generate permutations of different lengths.
        *   For example, there are also 6 ABC permutations of length 2, it's just that one letter is left out each time: AB, AC, BA, BC, CA, and CB

*   The `itertools` library implements the method `permutations(iterable, r)`. This returns an iterator which generates all the permutations of length `r` from the elements of the `iterable`, with each permutation in the form of a `tuple` of length `r`:
    ```python
        from itertools import permutations
        for permutation in permutations("ABC", 3):
            print(permutation)
    ```
    ```
        ('A', 'B', 'C')
        ('A', 'C', 'B')
        ('B', 'A', 'C')
        ('B', 'C', 'A')
        ('C', 'A', 'B')
        ('C', 'B', 'A')
    ```

*   Similar to a permutation, a **combination** is also a grouping of some objects of a particular length. However, unlike a permutation, a combination doesn't care about the internal order of the elements.
    *   For example, given ABC, AB and BA would be considered the same combination

*   Therefore, there are 3 combinations of length 2 from those 3 letters: AB, AC, and BC.

*   Combinations are more useful for generating possible subsets of a superset, while permutations are more concerned with possible orderings

*   The `combinations(iterable, r)` method returns an iterator which generates all possible length `r` combinations of elements from `iterable`, once again in the form of a series of tuples

*   `product()` is very similar to `combinations()`, but rather than generating combinations of elements from the same group of objects, `product()` combines elements from many different groups of objects.
    
    *   It works by accepting any number of iterables and returns an iterator which generates combinations, again as tuples.
    
    *   Each combination will be made up of one element from each of the iterables you provided as arguments, ordered based on the ordering of the arguments
        ```python
            
            from itertools import product 
            for prod in product("ABC", "DEF"):
                print(prod)
        ```
        ```
            ('A', 'D')
            ('A', 'E')
            ('A', 'F')
            ('B', 'D')
            ('B', 'E')
            ('B', 'F')
            ('C', 'D')
            ('C', 'E')
            ('C', 'F')
        ```
*   We mentioned when comparing sequences to iterators that while there is no such thing as an infinite sequence, it is possible to iterate infinitely with iterators.
    
    *   One example of this is with the `cycle(iterable)` method. `cycle` takes an iterable and returns an iterator which simply steps through it over and over again, indefinitely.
    
    *   You had better have a `while` condition or `break` somewhere, or else your code will run for a looooooong time!
    
    *   Let's see two examples of printing `cycle("ABC")` 12 times before stopping:
        ```python
            from itertools import cycle
            COUNT = 12
            my_iterator = cycle("ABC")
            while COUNT:
                print(next(my_iterator))
                COUNT -= 1
        ```
        ```
            A
            B
            C
            A
            B
            C
            A
            B
            C
            A
            B
            C
        ```
        

*   `groupby()` is the last itertool we will look at. It is used to group elements of a sequence together by some criteria.
    
    *   It works by taking an iterable object and a `key` function, similar to `sorted()` (except that it is a required argument here, so you don't _need_ the `key=` optional parameter name, but can include it if you want)
    
    *   `groupby()` will call the `key` function on each element of the iterable and group together elements which return the same value. `groupby()` outputs an iterator which generates 2-tuples, each one representing a grouping: index 0 is the value which this group was sorted by, and index 1 is another iterable containing the elements in the group.
    
    *   See it in action below:
        ```python
            from itertools import groupby
            
            def get_first_letter(x):
                return x[0]
            
            my_iterable = groupby(("AB", "AD", "BA", "BC", "BD", "DD"), get_first_letter)
            for category, contents in my_iterable:
                # contents is an iterable, so needs to be converted into a list
                print(category, list(contents))
        ```
        ```
            A ['AB', 'AD']
            B ['BA', 'BC', 'BD']
            D ['DD']
        ```


### **Itertools Summary:**

We looked at different methods from the `itertools` library. Each one returns an `iterator`.

*   A permutation is an ordering of values of some length from a group of values. The `itertools.permutations(iterable, r)` method generates all permutations of length `r` from items in `iterable`.

*   A combination is a subset of some elements from a superset, where order has no significance. The `itertools.combinations(iterable, r)` method generates all combinations of length `r` from items in `iterable`.

*   The `itertools.products(*iterables)` method generates all possible combinations of a single item for each of the supplied `iterables` (i.e. zero or more iterables), sorted based on the order of those iterables.

*   The `itertools.cycle(iterable)` method generates an iterator which will loop through `iterable` infinitely, cycling from the end back to the beginning.

*   The `itertools.groupby(iterable, key)` method groups elements of the `iterable` together based on matches in the value generated by the `key` function
