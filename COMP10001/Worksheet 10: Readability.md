Worksheet 10: Readability
=========================

**Date:** March 27, 2024

**Subject:** COMP10001

Commenting:
-----------

*   In Python, a comment is created by inserting the `#` character (number sign/hash symbol). After the `#` everything else on that line of code will be considered part of the comment and ignored by the computer.

*   There is no way to end a Python comment on a line once it has started.

*   Concerning how to decide when to comment in a program:
    
    *   _A comment for every 'step' towards solving the problem._
    
    *   That is, you should group related lines of code together into one or more 'steps', each taking a significant step towards solving the problem.
    
    *   Then, every step should have a comment to help a reader identify and understand it.

*   Here's another guiding principle about adding helpful comments to a program, concerning how to decide what to say in a comment:
    
    *   _Say why, not how._
    
    *   That is, you should use comments to explain the idea behind what your code is doing, not the details of how it does that

*   Just as code needs comments, our functions do too. For functions it's conventional to write a block of comments under the function definition and encased in `'''` triple quotes `'''`. This is called a **docstring** and is a requirement for each function you write in projects for this subject.

*   eg:
    ```python
        def ave_len(words):
            """ Accepts a sequence of strings `words` as input and returns
            the average length of strings in that sequence as a float.
            """
            count = 0
            for word in words:
                count += len(word)
            return count/len(words)
    ```

*   When you write **docstrings**, remember that they need to convey:
    
    1.  What the inputs to the function are
    
    2.  What the function does
    
    3.  What the return value is. If referring to variables or parameters in your docstring, it is convention to surround them with backticks ` ``` `

*   eg:
    ```python
        def shuffle(my_list):
            """ Accepts a list of integers `my_list` as input
            and mutates it by swapping values at index 2 and 3.
            Returns the sum of the two swapped integers.
            """
            temp = my_list[3] 
            my_list[3] = my_list[2]
            my_list[2] = temp
            return my_list[2] + my_list[3]
    ```

*   In more complex, longer functions, you won't be able to go into as much detail because docstrings shouldn't be lines and lines long, but try to give an overview of the function which would help someone attempting to use it.

Naming:
-------

*   Ideally, a reader should be able to understand the role a function or variable plays in a piece of code instantly, just by looking at the name. No extra comments should be required!

*   The following are some tips for choosing good function and variable names:
    
    *   Meaningful, not generic. It makes the purpose of the variable and its value in the program, or the action performed by the function immediately clear.
    
    *   For example:
        
        *   Store a user's name in a variable called name, not a generic name like string or value.
        
        *   Store a list of the colour-values of nearby pixels in nearby\_colour\_values or nearby\_values, not just my\_list (or even worse: a).
    
    *   Obvious, not obscure. Avoid making your own abbreviations; the meaning of the name should be immediately clear.
    
    *   For example:
        
        *   Store a user's name in a variable called name, not an abbreviated name like nm or n or something else.
        
        *   Store an image object in a variable called image (or something even more specific to the problem, like original\_image) rather than im or i.
        
        *   Store the a colour-to-be-highlighted in a variable called highlight\_colour, not hc or h.
        
        *   Call your function average(), mean(), or, if you must, avg(), but not av() or a().
    
    *   Some common abbreviations are acceptable (for example, max\_speed() instead of maximum\_speed()) but abbreviations should typically be avoided.

*   Importantly, you should not use one-letter variable or function names, apart from conventions understood by all programmers (such as the names of loop variables in range-based for loops), in mathematical contexts (such as using x and y to store coordinates), or in lambda expressions.

*   We can take this idea one step further, and use variables and functions as a way to explain code where we otherwise would have no named variables. For example, we can use variables to eliminate magic numbers.

*   Magic numbers are any literal numbers written into a program (and not on their own in a variable assignment). For example, the literals 120 and 3 in the program:
    ```python
        from turtle import *
        
        for i in range(3):
            forward(120)
            right(120)
    ```

*   Since literal values have no name, they can cause problems for readability. While we might understand the purposes of these numbers when we first write the program, it's easy to forget, for example, that one of those 120s represents the side length of a triangle, and the other represents an interior angle. And that 3, where did that come from? What significance does it have to the program? It may not be immediately obvious that this 3 is used to represent the number of sides of a triangle.

*   By using variables, we could make these ideas more obvious:
    ```python
        from turtle import *
        
        SIDE_LENGTH = 120
        NUMBER_SIDES = 3
        INTERIOR_ANGLE = 120
        
        for i in range(NUMBER_SIDES):
            forward(SIDE_LENGTH)
            right(INTERIOR_ANGLE)
    ```

>[!Tip]
>**Invariable variables (Constants)**
>By using a variable to give a name to a magic number, we are creating a variable whose assigned value will never actually change. Such a variable is called a constant, since its value is constant throughout the program.
>Conventionally, Python programmers use uppercase variable names to name constants. This doesn't give them any different properties as far as Python is aware, but it visually sets them apart from the regular variables in the program. This makes it more clear to a reader that the variables in use are just fixed values given a meaningful name. That's why the variable names in the above program are written with capital letters.

PEP 8:
------

*   Guidelines:
    
    *   Spacing:
        
        *   Line length must not exceed 79 characters.
        
        *   There should be no spaces between function/method names and arguments (also for slices and indexing) ie. write myfunc(arg) instead of myfunc (arg).
        
        *   Use blank lines between logically separate blocks of code (e.g. between functions and major sections associated with different comments). 2 blank lines are required after the end of a function.
        
        *   Do not write multiple statements on the same line. For example, Python allows a semicolon to be used to execute two lines of code in one a=1; b=3 Don't use this in your code because it will not comply with PEP8!
        
        *   Always start a new line after a statement containing if, elif, else, while, for, etc.
        
        *   Include spaces between arithmetic operators, i.e. write 2 \* 1 instead of 2\*1.
        
        *   To distinguish them from standard assignment, do not include spaces between (default) parameter names and values in a function definition, i.e. write def my\_function(myvar=1): instead of def my\_function(myvar = 1).
        
        *   Include a space after commas, for instance between elements of a list or tuple, or between arguments in a function call: (1, 2, 3) instead of (1,2,3).
        
        *   Use 4 spaces for indentation. (Grok does this by default. If you're having problems, check your editor preferences.)
        
        *   Don't use tab characters in your code. (Again, Grok is your friend here, in that it will automatically translate any tab-based indentation into spaces.)
    
    *   Commenting:
        
        *   Keep the indentation level of any comments the same as the line of code it is associated with.
        
        *   Do not state the obvious in comments.
        
        *   Do not use docstrings ('''these green comments''') for anything other than function documentation. Use block comments (# the red ones) for everything else.
    
    *   More Readability:
        *   When comparing booleans in conditional statements, it's clearer to write if cond:, rather than if cond == True, and it's clearer to write if not cond: rather than if cond == False:.

*   PEP8 mandates that lines must not be more than 79 characters long.
    
    *   With nice super-clear, unabbreviated variable names, our lines can get long, so what happens if they go over the character limit?
    
    *   Well there's a great solution for that.
    
    *   If you want a statement to continue over multiple lines you can write a backslash (, sometimes called an escape character) at the end of the line, and continue writing.
    
    *   eg:
        ```python
            my_really_really_clear_name = 7 * 4 + 4 + 4 + 9 * 4 +\
                                            4 - 3 - 3 - 3 - 3 - 3
            print(my_really_really_clear_name)
        ```

### Readability Summary:

We've learned about how readability of the code we write is important, and looked at some guidelines to ensure the code we write is easy to understand:

*   Programs are read more times than they are written, so we must work to make sure our programs are as readable as possible. `# a comment`

*   Comments are human-readable notes written in between lines of code which describe what the code is intended to do. They are ignored by the computer and are purely to aid human readability of code. Python comments are written starting with a # character.

*   As a rule of thumb, a comment should be written for every step towards solving a problem, with lines of code grouped together into these logical steps.

*   Comments should communicate the ideas behind your code, rather than explaining what it does in detail. Anyone reading your code will understand Python syntax so will be focused on how to interpret your choices, not how to understand how Python works.
    ```python
        def my_func():
            """This is a docstring"""
    ```

*   A docstring is a comment for a function, written inside `'''` triple quotes `'''`. It is intended to help someone else understand how to use our function. A docstring should explain:
    
    1.  What the inputs to the function are;
    
    2.  What the function does; and
    
    3.  What the return value is.

*   Meaningful variable and function names are another important part of writing readable code.

*   Variable and function names should communicate what they store or do, and should not be generic, obscure, or abbreviated.
    ```python
        NUMBER_OF_SIDES = 3
    ```

*   Magic numbers are any literal numbers written into a program. Variables should be used to name magic numbers to make their meaning obvious. There is a convention to name them with CAPITALS to indicate that their value does not change.

*   Overly complex expressions should be avoided. If they are necessary, they should be separated into their own functions.

*   Python has a style guide called PEP 8 which we will be following for the remaining worksheets and the projects

*   Long lines of code can be split into two lines using the `\` escape character.
