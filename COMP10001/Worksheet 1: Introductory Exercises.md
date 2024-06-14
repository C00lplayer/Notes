Worksheet 1: Introductory Exercises
===================================

**Date:** March 3, 2024

**Subject:** COMP10001



Basic Expressions
=================

*   The print() command displays message to the person running the program
    *   The output must be placed inside quotation marks like _`(" insert text ")`_

*   Python can also do numerical calculations:
    
    *   Asterisk ‘`*`’ is multiplication
    
    *   Plus ‘`+`’ is addition
    
    *   Minus ‘`-`’ is subtraction
    
    *   Slashes ‘`/`’ is division

*   Python also handles order of operations
    
    *   In programming terms, we say that multiplication has a **higher precedence** than addition and subtraction
    
    *   When two operations have the same precedence, such as addition and subtraction, the left one is done before the right one.
    
    *   You can use round brackets (also called **parentheses**) to make the order of operations explicit

*   The operators `+`, `-`, `*` and `/` which we have seen so far work with two numbers: one on either side of the symbol. These are called **binary operators**
    
    *   `+` and `-` are unique in that they can also be used with just one single number.
    
    *   Operators applied to only one number are called **unary operators**.
    
    *   In this context, `+` and `-` function in a similar manner to putting a positive or negative sign in front of a number in maths: `-` will change the sign from positive to negative or vice versa; but `+` is fairly useless and won't change the number at all.

*   A **comment** is a plain language description of what a block of code does which is only intended to be read by a human; the Python interpreter simply ignores all comments.

    *   A `#` character indicates the start of a comment.

*   We say that the quotation marks act as **delimiters**, which means they mark the start and end limits of pieces of text which the command outputs and doesn’t interpret
    
    *   The word **string** is used to describe a piece of text inside quotes.
    
    *   Strings can be surrounded in either single quotation marks (`'`) or double quotation marks (`"`), providing that the same ones are used at the start and end of a particular string

*   One elegant aspect of Python is that it allows you to perform calculator-like operations on strings. For example, you can "add" two strings together using the `+` operator:
    *   _`print("Hello" + "World")`_ makes an output of _`"HelloWorld"`_

*   When applied to strings, the `+` operation is called **concatenation**
    *   Notice that concatenation doesn't do anything clever like insert a space between the words.

*   The same thing can be used with multiplication:
    
    *   _`print('Hi' + 'Hi' + 'Hi')`_ makes an output of _`"HiHiHi"`_
    
    *   _`print('Hi' * 3)`_ makes an output of _`"HiHiHi"`_

*   You can store and reuse a previously computed **value** using a **variable**

*   Variables are created in Python using an operation called **assignment** which gives the variable the value it should remember:
    ```python
        message = "Hello world"
        print(message)
    ```
    *   In the first line above a variable called `message` is created, and the value `'Hello World'` (a string of text) is assigned to it
    
    *   A value which is typed directly into a program like `'Hello World'` here is called a **literal**
    
    *   The `=` symbol is called the **assignment operator**, which assigns the value of the expression on the right to the variable on the left
    
    *   Note that the variable is referred to by its name, which is `message`, but the variable name is not printed: its _value_ is printed
    
    *   The technical word for the _name_ of a variable is **identifier**

*   Note that you can also assign a new value to a variable just by using assignment again:
    ```python
        msg = 'Bye'
        msg = msg * 2 
        print(msg)
    ```
    *   In the above example, the following three operations are performed in order:
        
        1. The string `'Bye'` is assigned to the variable `msg`.
        
        2.  The expression _`msg * 2`_ is calculated, using the current value of `msg`. This gives the string `'ByeBye'`. This new value is assigned to the variable `msg`, thus overwriting its old value with the new one.
        
        3.  The value of `msg` is printed out, giving the output _`ByeBye`_.

*   When a variable is assigned a new value, its old value is forgotten

*   There are certain rules for naming variables like:

    
    1.  Variable names must start with either an alphabetic letter or an underscore (`_`).
    
    2.  The rest of the name can contain zero or more occurrences of the following things:
        
        *   Digits (`0` to `9`).
        
        *   Alphabetic letters.
        
        *   Underscores.
    
    3.  Nothing else is allowed in a variable name. Here is a (incomplete) list of the things you can't use anywhere in a variable name:
        
        *   Whitespace characters (the space, tab, new line).
        
        *   Hyphens (`-`)
        
        *   Quotation marks (` ' ` or ` " `)
        
        *   Symbol characters such as: the question mark `?`, the exclamation mark `!`, brackets `()`, and so forth.
    
    4.  The following words having special meaning in Python, and so they cannot be used for variable names: `and`, `as`, `assert`, `break`, `class`, `continue`, `def`, `del`, `elif`, `else`, `except`, `False`, `finally`, `for`, `from`, `global`, `if`, `import`, `in`, `is`, `lambda`, `None`, `nonlocal`, `not`, `or`, `pass`, `raise`, `return`, `True`, `try`, `while`, `with`, `yield`.

*   Python has a built-in function called _`input()`_ that can be used to get keyboard input from the user as a string.

*   The `input` function can be given a message to display, usually prompting the user with what kind of information the program wants

*   The most basic kind of mistake you can make is a **syntax error**.
    *   A syntax error occurs when you type something which is not properly formed, according to the rules of the programming language. It is the same as make (sic!) a grammatical error in English (or any natural language for that matter).

### Summary:

*   A computed or entered value can be saved inside a **variable** which is a name used to reference it.

*   Saving a value into a variable is achieved using the `=` **assignment** operator.

*   Except for a few rules (below) you may name variables however they wish, with the strong suggestion that they be meaningful names which match the data stored.

*   The value stored in a variable may be overwritten by assigning a new value with the `=` operator.

*   The _`input()`_ function can be used to take input from the user.

*   A string prompt be entered between the brackets (similar to _`print()`_) which is shown as a prompt for the user entering their text.

*   The text which is entered by the user is stored as a string and can be assigned to a variable with the `=` operator.

*   Multiple values can be given to the _`print()`_ function by separating them with a comma. They will then be displayed with a space between them.

*   Variable names must:

    *   Start with an underscore or a letter

    *   Contain a combination of letters, numbers or underscores
      
    *   Not contain any hyphens, spaces or other symbols
      
    *   Not be words which have special meanings in Python. These are words such as `import` and `else`
