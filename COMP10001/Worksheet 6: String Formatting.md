Worksheet 6: String Formatting
==============================

**Date:** March 13, 2024

**Subject:** COMP10001

String Formatting:
------------------

*   Using f-strings allows to enter variables inside strings in a more efficient manner by using the {} to seperate the variables from the string

*   For floating point numbers (i.e. numbers of type float), f-strings allow even finer control. By placing a colon `:` after the value inside braces, we can use a format specifier which looks like this: `6.2f`.
    
    *   Breaking down the above format specifier, the 6 indicates that this value should be formatted to take up a 6-character window of space in the f-string
    
    *   The .2 indicates that the number should display 2 values to the right of the decimal point
    
    *   And the f indicates that the number displayed is a floating point number.

*   Floating point formatting is especially useful when we want to align numbers with different amounts of decimal places so that we can read them more easily. Compare below with and without f-strings:
```python
    print(20)
    print(9.7)
    print(13.0053)
    print(0.05)
    
    print("With f-strings:")
    print(f"{20:5.2f}")
    print(f"{9.7:5.2f}")
    print(f"{13.0053:5.2f}")
    print(f"{0.05:5.2f}")
```
```
    20
    9.7
    13.0053
    0.05
    
    With f-strings:
    20.00
     9.70
    13.01
     0.05
```

>[!Tip]
>Putting a 0 at the start of the format specifier will fill padded blank spaces with zeros instead:
>  ```python
>  print(f"{20:05.2f}")
>  print(f"{9.7:05.2f}")
>  print(f"{13.0053:05.2f}")
>  print(f"{0.05:05.2f}")
>  ```
>  ```
>  20.00
>  09.70
>  13.01
>  00.05
>  ```

*   Just like we formatted floats on the last slide, we can also format strings using the same notation. For strings, the number after the decimal point indicates how many characters from the string to include in the formatted output, and s replaces the f we used for floats.

>[!Tip]
>For numbers, alignment defaults to the right of the window it has allocated. Putting a < at the front of a format specifier instead aligns the formatted number to the left of the space:
>```python
>print(f'{1.5:7.1f}')
>print(f'{1.5:<7.1f}') # Formats left
>```
>```
>1.5
>1.5
>```
>For strings, alignment defaults to the left. Try > to format it to the right.
>```python
>print(f'{"big long string":5.2s}')
>print(f'{"big long string":>5.2s}') # Formats right
>```
>```
>bi
>    bi
>```
>There's also a third option! ^ will position the value in the centre of the window:
>```python
>f'{1.5:^7.1f}'
>f'{"big long string":^5.2s}'
>```

*   `g` indicates "optimal notation" where python chooses the best amount of decimal places for the number supplied if not given a specific amount of characters to format to

*   `d` is the value specifier for standard decimal numbers (integers). A comma can be added before it to add thousands-separating commas to the number.

*   The `c` character format code also takes an integer but displays it as a character based on the Unicode standard

*   If you want to use a variable inside a format specifier - perhaps to calculate the window for a particular value - you need to surround it in another set of braces because otherwise Python will only accept literal values.
```python
    print(f'{text:^{window}s}')
```
*   As `window` is a variable it must be placed inside the curly braces `{}`


### String Formatting Summary:

We have seen how we can format strings using f-strings. f-strings are all about putting objects in the right place to get nicely styled output.

*   An f-string is written by prepending f to the start of a string, before the quote.

*   Inside an f-string, a variable can be inserted by writing it inside a pair of braces {}.

*   A format specifier can be included for each inserted value controlling how it is formatted in the resultant string.

*   For example:
```python
    print(f"A float: {4.35:<05.5f}")
```
*   To summarise all the parts and options of a format specifier, look at the table below, which breaks down an example specifier `:<05.5f`

|**Part**|**Meaning**|**Alternatives**|
|--------|-----------|----------------|
|`:`|Separates value from format specifier|Required, unless you're not using a format specifier at all|
|`<`|Aligns formatted text to the left|`>` aligns to the right, `^` centres text, If not specified, defaults to right for numbers and left for strings, For numbers, a comma `,` can be added to format it with thousand-separating commas|
|`0`|Fills extra space with zeros. Only allowed for numbers.|If not specified, defaults to spaces|
|`5`|Sets the formatted window to be five (or whatever integer value you provide) characters long| If not specified, the window will simply be equal to the length of the formatted value
|`.5`|Precision: formats the number to five (or whatever integer value you provide) decimal places, and truncates the rest.|For strings, indicates number of characters from string to include   If not specified, performs no truncation on the value  
|`f`|Format code: specifies that data should be interpreted as a float|`s` for string,`g` for "optimal" float notation, `d` for integer, `c` for Unicode character, If not specified, infers type|
