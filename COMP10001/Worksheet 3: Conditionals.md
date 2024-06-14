Worksheet 3: Conditionals
=========================

Date

@March 11, 2024

Finished?

Subject

[![](https://www.notion.so/icons/bookmark_red.svg)COMP10001](https://www.notion.so/COMP10001-9b459138d39749a4926cfa6e4e260d8d?pvs=21)

Type of Class

Assignment/Worksheet

Week

Week 3

Conditionals:
-------------

*   In order to be able to change the behavior of our code on different conditions, we need three things:
    
    1.  A way of expressing truth, to store whether a given condition holds or not. This means storing a yes or no value in Python.
    
    2.  A way of testing for a given condition, often based on comparison between values, e.g. testing for the number being between 1 and 5.
    
    3.  A way of only running code when a given condition holds, e.g. if a number is between 1 and 5 it will output that exact number

Boolean Variables:
------------------

*   A Boolean is a way of expressing the outcome of a condition or a test
    *   It holds one of the two truth values: True or False

*   To convert something to boolean, i.e type conversion, you use `bool()`

*   Normally the “default” value converts to false and everything else to true:

    print(bool(1))
    print(bool(-2.0))
    print(bool("False"))
    print(bool(0))
    print(bool(0.0))
    print(bool(""))
    print(bool(False))

Which outputs:

    True
    True
    True
    False
    False
    False
    False
    

Relational and Logical Operators:
---------------------------------

*   Python supports six relational operators, summarized in the following table:

**Python**

**Meaning**

**Math Notation**

<

less than

<

<=

less than or equal

≤

\==

equal

\=

!=

not equal

≠

\>

greater than

\>

\>=

greater than or equal

≥

*   When used it evaluates/outputs as a Boolean
    *   This relational operators can also be used between `int` and `float` data types

❗

The equality relational operator `==` is particularly worthy of note, as it is the source of many a bug when you first start coding, due to confusion with the assignment operator `=`.

*   These relational operators can also be applied to strings
    
    *   In general, strings are compared and sorted by their alphabetical order.
    
    *   But be aware that all lowercase letters are considered greater than uppercase letters

*   Characters have numbers associated with them which can be accessed through the `ord()` method. This can be used to tell if one character is greater than another. e.g.: 
    
        print(ord('A'))
        print(ord('a'))
        print('a' > 'A')
    
        65
        97
        True
    
    *   Since `ord('A')` returned 65 and `ord('a')` returned 97, `print('a' > 'A')` is equivalent to `print(97 > 65)`

*   Another test we can perform on strings is whether one is a subset of another by using the operator `in` , which is also called a test for membership:
    
        print('Hell' in 'Hello')
        print('hell' in 'Hello')
        print('moo' in 'wooloomooloo')
        print('wooloomooloo' in 'moo')
    
        True
        False
        True
        False
    
    *   As seen from above it is case sensitive and the ordering of the string also matters

*   **Logical expressions** are expressions which evaluate to a `bool` value. For instance, an expression using relational operators like `3 < 5` is a logical expression

*   When combining logical expression tests we use logical operators:
    
    *   Python has two binary logical operators (that apply to two Boolean variables) — >`and` and `or` 
    
    *   And one unary logical operator (that applies to a single Boolean variable) —> `not`, The `not` operator negates the logical expression it is applied to

The rules for `and` and `or` are summarized as follows:

**Operands**

**Logical Operator**

**A**

**B**

**A** `**and**` **B**

**A** `**or**` **B**

`False`

`False`

`False`

`False`

`True`

`False`

`False`

`True`

`False`

`True`

`False`

`True`

`True`

`True`

`True`

`True`

*   Python also has an order it follows: that is, relational operators are evaluated first, followed by `not`, etc
    *   It's very easy to get confused about operator precedence in logical expressions, so the best thing is to use parentheses to make the precedence clear

*   One thing you will occasionally want to do is check whether a given variable falls within a range

*   As a shorthand, Python offers a second way of expressing the same thing (very close to the mathematical notation):
    
        n = 4
        print(0 < n < 6)
    
        True
    
    *   In fact, it is possible to multiply "stack" relational operators, e.g.:
        
            print('A' < 'Z' < 'a' < 'z')
        
            True
        

### Boolean and Logical Operator Summary:

*   We have seen the first two of three tools we need to make code which behaves differently in different circumstances:

1.  a way of expressing truth, to store whether a given condition holds or not.
    
    *   This is done with **Boolean** values which can only be either true or false.
    
    *   In Python the `bool` type holds one boolean value, either `True` or `False`
    
    *   Other types can be converted to `bool` with the `bool()` function. The number zero or an empty string will convert to `False`; any other value will convert to `True`.

2.  a way of testing for a given condition, often based on comparison between values
    
    *   Python's six **relational operators** (`>=`, `>`, `==`, `!=`, `<`, `<=`) compare two values, evaluating to a boolean result.
    
    *   It's especially common to confuse equality `==` and assignment `=` operators, so watch out for this.
    
    *   `in` can be used to test whether a substring is contained inside a superstring.
    
    *   A **logical expression** is any expression which evaluates to a `bool` result.
    
    *   Python's three **logical operators** `and`, `or` and `not` combine boolean values, or the results of logical expressions.
    
    *   `and` and `or` are **binary** operators, combining two boolean values into one. `not` is a **unary** operator, negating one particular boolean value.
    
    *   Python defines precedence over logical and relational operators as follows, from highest to lowest precedence: relational operators (including `in`) > `not` > `and` > `or`. Brackets are advised to make the order explicit.
    
    *   It is possible to chain relational operators to test for more complex ranges.

If Statements:
--------------

*   Normally if statement test for a condition and if that condition holds it follows a set of instructions, this has a structure of:
    
        if <condition>:
            <block of statements>
    

*   The `condition` is usually a logical expression, involving relational or logical operators.

*   The block of statements followed is indented to the `if` statement
    
    *   (i.e. there is extra white space at the start of the line to offset it from the `if` statement it is attached to). This is how Python knows what code to run when the `if` condition evaluates to `True`. If there were more lines of code associated with the `if` statement, they would similarly be indented
    
    *   While indentation can technically be as many spaces as you like, to follow good Python style practices, you should make all of your indents **four spaces** long

*   The combined set of indented statements underneath the `if` line is termed a **block**  
      
    

💡

We said above that the condition in an `if` statement "is **usually** a logical expression". Well, the condition **must** be an expression, because it must evaluate to something. But while it's most natural for it to be a logical expression (when we use `if` we're normally testing some condition to generate a truth result) Python allows the condition to evaluate to any data type you like.  
If the condition doesn't evaluate to a   
`bool`, Python will implicitly convert it into a `bool`. That is, the zero or empty value of a data type (`0`, `0.0`, `''`) will evaluate to `False` and everything else `True`.  
So,  
  
`if "hello":`  
works, and is equivalent to  
  
`if bool("hello"):`  
meaning it will trigger every time since   
`bool('hello')` will always evaluate to `True`. We will see some more clever uses of this in the future.

*   If you need to decide between two alternatives, Python provides the `if-else` statement

*   If the condition evaluates to `True`, the first indented block of statements will be executed, otherwise the alternative block will be executed. In summary: an `if-else` statement can model a two-way decision.

*   If you want to decide with more than one condition you can use the `elif` statement:
    
        if <condition1>:
            <block 1 of statements>
        elif <condition2>:
            <block 2 of statements>
        elif <condition3>:
            <block 3 of statements>
        ...
        else:
            <block n of statements>
    

*   In a multi-way if statement, at most one of the indented blocks will run.
    
    *   The conditions are tried in order until one is found that evaluates to True.
    
    *   The associated block of code is run and any remaining conditions and blocks are skipped.
    
    *   If none of the conditions are True but there is an else block, then Python runs the else block.

### if Statement Summary:

*   We have looked at the last of the three tools we need to make code which behaves differently in different circumstances: a way of only running code when a given condition holds:
    
    *   The if statement can be used to run a block of code only if a particular condition (usually a logical expression) evaluates to True.
    
    *   The lines of code associated with an if statement are called a block.
    
    *   To specify that a block is associated with a particular if statement, each line of that block must be indented by the same amount of spaces on the lines immediately below the if. In this subject, you should always use four spaces of indentation.
    
    *   An else statement can be included after if to specify an alternative block of code to execute in the scenario that if's condition evaluates to False.
    
    *   Multiple elif statements can be used after if to specify alternate tests to be tried if all of the previous ones evaluate to False.
    
    *   It is important to always consider including an else clause to avoid forgetting about any scenarios not covered by your if and elif conditions.

*   The general form of an if statement is below:
    
        if <condition>:
        <block of code>
        elif <condition 2>:
        <block of code>
        ...
        else:
        <block of code>
