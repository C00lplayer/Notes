Worksheet 4: Sequences
======================

**Date:** March 12, 2024

**Subject:** COMP10001

String Indexing
---------------

*   Strings are **sequences** of characters

*   Python numbers the position of each character within a string, starting with the first character at position number 0, and proceeding sequentially from left to right

*   For example, the different characters in the string `"Python"` are numbered as follows:

|**character**|`P`|`y`|`t`|`h`|`o`|`n`|
|---------|---|---|---|---|---|---|
|**index**|`0`|`1`|`2`|`3`|`4`|`5`|
    
*   To access a character at a particular position, we can specify its position number inside square brackets.
    
    *   This technique is called **indexing** or **subscripting** the string.
    
    *   The position we specify inside the square brackets is called the **index**

*   For example:
    ```python
        s = "The number is 42."
        print(s[0])
        print(s[1])
    ```
    ```
        T
        h
    ```

*   The index `0` returns the first letter of the string and so forth

*   Indexing also includes blank spaces and full stops

*   The largest valid index is one less than the length of the string (remember that we start counting from `0`).

*   Python has a built-in function for that purpose: the `len()` function
    *   Note that `len()` works a bit like the `print()` function: you give it the string you want to measure the length of inside parentheses. However, unlike the `print()` function (which has no output) the output of `len()` is an `int`: the number of characters in the string.

*   Negative indices can be used to extract characters from the end of the string
    *   so `-1` indexes the last character, and `-17` indexes the 17th last character

*   Returning to our example of `"Python"` from earlier, the negative index of each character is as follows:

|**character**|`P`|`y`|`t`|`h`|`o`|`n`|
|---------|---|---|---|---|---|---|
|**index**|`-6`|`=5`|`-4`|`-3`|`-2`|`-1`|

*   When extracting more than one character Python provides a convenient method to access a substring: you simply need to specify a start and **(non-inclusive)** end index
    *   This method is also known as **slicing**

*   You can also slice with negative indices. The same basic rule of starting from the start index and stopping one before the end index applies

*   Python provides two shortcuts for common slice values:
    
    1.  if the start index is 0 then you can leave it blank
    
    2.  if the end index is the length of the string then you can leave it blank

*   You can specify a third number in a slice (after a second colon) which indicates how much to step through the sequence by for each item included in the slice.
    *   By default, this number is `1`, indicating that **every** element should be included. If, instead of every item you wanted **every second** one, you can use a step value of `2`

*   If the step is -1, it reverses the direction of the sequence you are slicing.
    *   Note that the direction of the indices must be changed also (the rightmost character is now the start index and the leftmost is the end index)

### Indexing and Slicing Summary:

*   We have introduced sequences and looked at how we can index and slice strings as a sequential type we are familiar with:
    
    *   Sequences are data types which contain an ordered collection of many things. Strings are a sequence of characters.
    
    *   The items in a sequence are numbered starting at 0 for the leftmost one and increasing, or -1 for the rightmost one and decreasing
    
    *   **Indexing** or **Subscripting** allows for a particular item to be extracted from a sequence. This is done by putting the index of that item square brackets.
        ```python
            print("let's index"[2])
        ```
    
    *   Attempting to index beyond the length of a sequence results in an `IndexError`.
    
    *   The `len()` function can be used to find the length of a sequence by inserting the sequence between the brackets. It returns the sequence's length as an `int`.
    
    *   A **slice** is a subsequence of some sequence. Slicing is performed by writing the start index, a colon `:` and the end index inside square brackets.
         ```python
            print("let's slice"[4:7])
         ```
    
    *   Slicing starts with the item at the start index and takes all items up to **but not including** the one at the end index.
    
    *   If the start index is the start of the string you can leave it blank; if the end index is the end of the string you can leave it blank.
    
    *   A third "step" number can be added to a slice after a second colon, controlling how often items from the sequence are added to the slice. A step of -1 reverses the sequence.
    
    *   An empty slice or a slice over indices which don't exist returns an empty sequence.
    
    **Extension to Lists and tuples:**
    ----------------------------------
    

*   The second kind of sequence we will look at is called a `list`

*   Lists are for storing sequences of possibly different objects. You might, for example, want to store a list of words, to find which one was the longest. Or you might want to store a list of numbers, such as the costs of different items. Or maybe lists of both like:
     ```python
        my_words = ['pig', 'pineapple', 'panoply', 'polyp']
        my_costs = [5.0, 12.0, 200000000.59]
        my_jumble = ['jumbly', 4, 'wumbly', 'number', 5]
    ```

*   Lists are delimited with square brackets and individual items are separated by a comma. It is good style to include a space after each comma when writing lists to make them easier to read.

*   You can find the length of lists:
 ```python
    my_jumble = ['jumbly', 'wumbly', 'number', 5]
    print(len(my_jumble))
 ```

* Which gives: `4`

*   All of the operations which we were able to perform with strings will work with lists and tuples too.
    *   These include ability to concatenate strings (join them together with the + operator), and multiply them (\*)

*   The `in` operator also works for lists and tuples. We could generalise it as a test for the membership of a sub-sequence in a super-sequence

*   Finally, `min()` and `max()` are handy functions which may be used with sequences.
    
    *   They return the "minimum" or "maximum" element of a sequence, respectively.
    
    *   For numbers, this means the smallest or largest number
    
    *   But for string min outputs the earliest letter of the alphabet and max outputs the latter letter of the alphabet

*   The final kind of sequence we will look at is a `tuple`

*   This is essentially the same as a list in that it can contain any combination of objects, but it can't be changed after creation (it is **immutable**)

*   A tuple is defined similarly to a list, but with round brackets (or "parentheses")

*   Lists and tuples allow us to store anything we like inside of them this includes another lists
    
    *   This would be called a **nested list**.
    
    *   Any sequence stored inside another is called a **nested sequence**.

*   Elements of nested sequences can be accessed by indexing twice.
    
    *   The first index is to return the nested sequence from the list or tuple it is contained in.
    
    *   The second index is to return the element we want from that nested sequence

*   We can take this another level and index or slice strings

For example:
 ```python
    my_tuple= ('name', 3, ['a', 'nested', 'list'], 'age')
    print(my_tuple[2])
    print(my_tuple[2][1])
    print(my_tuple[2][1][:4])
```
```
    ['a', 'nested', 'list']
    nested
    nest
```
### Lists and Tuples Summary:

*   Lists are sequences of any values.

*   Lists are delimited with square brackets `[]` and individual elements are separated with a comma , e.g. `[1, 2, 3]`

*   An empty list is written as `[]`. A list with one item is written as `['item']`.

*   Tuples are sequences of any values, though they may not be changed after creation

*   Tuples are delimited with round brackets `()` and individual elements are separated with a comma , e.g. `(1, 2, 3)`

*   An empty tuple is written as `()`. A tuple with one item must be written with a comma after that item `('item',)`

*   Sequential operations indexing, slicing, len(), the in operator and the sequential + and \* operators work exactly the same for lists and tuples as they do for strings.

*   min() and max() can be used to find the minimum or maximum element, respectively, in a sequence.

*   Elements of a sequence which is nested inside another sequence can be accessed by indexing twice (first into the "containing" sequence, then into the "contained" sequence).
