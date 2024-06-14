Worksheet 2: Numerical Expressions
==================================

Date

@March 3, 2024

Finished?

Subject

[![](https://www.notion.so/icons/bookmark_red.svg)COMP10001](https://www.notion.so/COMP10001-9b459138d39749a4926cfa6e4e260d8d?pvs=21)

Type of Class

Assignment/Worksheet

Expressions and Data Types:
---------------------------

*   Two important structural terms for code are **statements** and **expressions**. These form the structure of each and every program.

*   A **statement** is any valid line of Python code. Think of it like a sentence in a book

*   An **expression** is, as a simplified definition, a statement which **evaluates** to some value
    
    *   All code involving numerical operators which we have seen so far are expressions, since they evaluate to the solution of the mathematical operation they're performing. 
    
    *   `9 + 11` and `3.0 / 4` are expressions.
    
    *   `input("Enter a number: ")` is also an expression as it will evaluate to the string input by the user.

    x = 25          # a statement
    x = x + 10      # an expression
    
    print(x)

*   All expressions are statements, but not all statements are expressions.
    
    *   Only statements which evaluate to some value are expressions. 
    
    *   `(2 + 3) * (5 - 7)` is both an expression and a statement.

*   A statement can contain multiple expressions, for example `(2 + 3) * (5 - 7)` is a single statement (one line of code) but contains three expressions: one with `+`, one with `-` and one with `*`.

*   Expressions themselves can be made of multiple expressions: again looking at  `(2 + 3) * (5 - 7)`, it is an expression containing three sub-expressions.

*   The most common way we've seen to make some code evaluate to some result is by using an **operator**.

*   Recall that we've looked at four operators so far: `+`, `-`, `*` and `/`.
    *   In an arithmetic sense, they perform a calculation using two numbers, which are written on either side of the operator. These numbers are known as **operands**.

*   A **simple expression** is an expression containing one operator and its operands.

*   Because simple expressions return a value, they could be used to construct more expressions, such as `(3 + 5) / (4 - 2)`.
    
    *   The two operands of `/` are simple expressions whose result will be used to calculate the division.
    
    *   But an expression with expressions inside it is no longer a simple expression, but rather a **compound** expression.
    
    *   You could continue to replace numbers by expressions infinitely, making even more complicated expressions!

*   To allow operators to behave differently when used with different types of data, Python gives a **data type** to every value we store

*   Data types include:

**Type**

**Description**

`int`

For whole numbers eg: `-3`, `-5`, or `10`

`float`

For real numbers eg: `-3.0`, `0.5`, or `3.14159`

`bool`

The Boolean type. For storing `True` and `False` (only those two values; Booleans allow for no grey areas!).

`str` (= "string")

For chunks of text, e.g.: `"Hello, I study Python"`

`tuple`

For combinations of objects, e.g.: `(1, 2, 3)` or `(1.0, "hello", "frank")`

`list`

A more powerful way of storing lists of objects, e.g. `[1, 3, 4]` or `[1.0, "hello", "frank"]`

`dict`

We will see this later ... maybe you can guess what it does, e.g. `{"bob": 34, "frankenstein": 203}`

*   Note that you can check the data type of any object with the `type` function. e.g:

    print(type("Can you make this print:"))

which outputs: `<class 'str'>` which shows the data type being ‘str’ also known as string

Integers and Floats:
--------------------

*   The data type `int` is a type for all positive and negative whole numbers (yes, and zero; i.e. all integers), such as ­`1` or `-1523`

💡

Python allows for underscores to be used inside numbers, acting like commas to make them easier to read.

The huge number `300000000000000000` in the print statement above might be hard to interpret, but we can instead write it as `300_000_000_000_000_000` which hopefully makes it a _little_ more clear to see that it's 300 quadrillion!

This is purely a visual aid for numbers which you write into python programs: when they are printed out, they don't have the underscores. The following two lines of code are equivalent:

*   The type `int` is distinct from the type `float`, which represents numbers with a decimal component such as ­`9.23`. These number are called **floating point numbers** and can approximate fractions

*   If a number has a decimal place, Python will interpret it as a `float`.

*   Another way of creating a `float` is scientific notation, e.g. `1e3`. The notation `1e3` is just a shorthand for 1\* 10^3:

*   If an integer is added/subtracted/multiplied to another integer is results in a variable with an integer data type

*   But if two integers are divided the resulting variable will be a variable with a data type of float

*   However if the operands are integers with a decimal point, each operand and the result becomes a float

*   This can be summarised in a table:

**Expression**

**Result**

`int`(`*`,`+`,`-`)`int`

`int`

`int/int`

`float`

`float`(`*`,`+`,`-`,`/`)`float`

`float`

`float`(`*`,`+`,`-`,`/`)`int`

`float`

`int`(`*`,`+`,-,`/`)`float`

`float`

*   A **rounding error** is the discrepancy between the approximated value and its exact value.

*   Floating point numbers allow us to represent a large set of numbers. Since there are infinitely many numbers (even in the range of -1 to 1) and the `float` data type has only a fixed amount of computer storage space available, some numbers will inevitably have rounding errors.

### Integers and Floats Summary:

*   **Statements** are the building blocks of a program. Every valid line of Python code is a statement.

*   **Expressions** are statements which evaluate to some value. They could be literal values or the mathematical operations or an instance the `input()` function.

*   A **simple expression** is an expression composed of an **operator** and its **operands** (generally two).

*   Each value in Python has an associated **data type** which defines the kind of information it stores.

We formally introduced two data types (in addition to `str` which we saw previously):

*   The `int` data type represents all positive and negative **integers** (whole numbers).

*   The `float` data type represents all **floating point numbers** which are those which contain a fractional part.

*   `float`s can be created by writing a number with a decimal point or by using the `e` scientific notation.

*   `float`s are approximations, and **rounding error** discrepancies are common when dealing with precise numbers.

We looked at which data types the basic operations return:

*   When the operands of addition, subtraction or multiplication are both `int`s, the result will always be an `int`.

*   When at least one operand of `+`,  or  is a `float`, the result will always be a `float`.

*   When using division, the result will always be a `float` regardless of whether the operands are `int`s or `float`s.

Type Conversions and Inputs:
----------------------------

*   Python provides an explicit means of converting one data type into another data type (if the conversion is possible). This conversion is also called **type casting**
    *   The function `int()` converts floating point numbers to integer values. It can also convert strings if all

*   Note that the conversion from a floating point number to an integer always truncates the fractional part, meaning that `32.0`, `32.5` and `32.999` all convert to `32`

*   However if you try to convert between data types when the conversion is not possible it fails
    *   Like the example below you cannot convert between the string type to integer type as the string contains the decimal point which is not a digit:

    print(int("32.7"))

*   The `float()` function returns the corresponding `float` value for the input:

    print(float(32))

*   `float()` is able to convert any string representation of an integer or floating point number into a `float`, including numbers written with scientific notation. This is an improvement over `int()` which could only convert strings containing digits.
    *   The following will all be successful in converting to float type:

    print(float("32.7"))
    print(float("32e4"))
    print(float("32"))

*   The function `str()` converts values to the type `str` (a string).

💡

To convert to a particular type, you just have to use the function with the same name as that type. This is consistent with all types, from `int()` all the way to `dict()` and `set()`!

*   `input()` always returns a string, so if your program requires a string as input, there is nothing more to do

*   If the input is a number, on the other hand, Python will see this as a string consisting of digits

*   We need a function that converts a string where each character is a digit, into a number. If your program expects integer values, you simply use the function `int()`:

    num = int(input('Enter a number to double: '))
    print('2 x', num, '=', 2 * num)

*   If your program expects floating point numbers, you would cast to a  `float`  using  `float()` instead.

More Operators:
---------------

*   You saw previously that the division operator `/` returns a `float` when applied to two integers.

*   However, there are instances where you want to rely on the result of a division being an integer, irrespective of the numbers involved.

*   This is called the **integer division** or **floor division** operator and in Python it is used with a double slash `//`, as seen in this example:
    
        print(13 // 4)
    
    *   which outputs `3`

*   Note that in integer division, the result is always rounded down to the nearest integer

*   However, if we divide thirteen people into three groups of four, there will be one person left over. The **modulo operator** `%` computes the **remainder** of an integer division. Here is an example of using modulo to calculate remainders:
    
        # Using the modulus operator
        print(13 % 4)
    
    *   Outputs `1`

*   Finally, to raise things to powers in Python (e.g. 47), we use the **exponentiation operator** `**`

*   Following the order of operations, exponentiation operations are performed _before_ any addition or subtraction operations.
    *   Also note how the exponentiation operator is generally used with no whitespace between the two numbers it applies to, unlike all other arithmetic operators:

    print(2**2)
    print(3**2)

### Type Conversions and Operator Summary:

*   **Type casting** is the process of converting a value from one data type to another.

*   Casting can be achieved by using the type's name as a function. For example, `int()` converts the value inside brackets into an integer.

*   The `input()` function always returns a string, so casting is a useful way to convert input text into your preferred type.

Some new arithmetic operators were introduced:

*   The `//` **integer division** or **floor division** operator performs division but returns the result as an `int` by truncating the fractional part.

*   The `%` **modulo** operator returns the remainder when the first operand is divided by the second.

*   The `*` **exponentiation** operator returns the value of the first operand raised to the power of the second.

After this worksheet, you should now feel comfortable using the three basic data types which we have introduced: `int`, `float` and `str`. Proceed to the next worksheet to use types in a range of different contexts.
