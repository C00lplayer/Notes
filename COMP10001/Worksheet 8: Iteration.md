Worksheet 8: Iteration
======================

Date

@March 18, 2024

Finished?

Subject

[![](https://www.notion.so/icons/bookmark_red.svg)COMP10001](https://www.notion.so/COMP10001-9b459138d39749a4926cfa6e4e260d8d?pvs=21)

Type of Class

Assignment/Worksheet

Week

Week 3

While Loops:
------------

*   Here is the code that provides the same output as before, based on the `while` statement.
    
        sec = 10
        
        while sec > 0:
        
            print(f'{sec} seconds to start!')
        
            sec = sec - 1
        
        print('Ignition complete. Launch initiated!')
    

*   Similar to the `if` statement, the `while` statement tests whether a condition — in our case `sec > 0` — evaluates to `True`.
    *   In the instance it evaluates to `True`, it executes the block of code associated with the `while` statement (again, akin to an `if` statement).

*   Where the difference lies is that instead of then proceeding to execute the code following the `if..elif..else` block, the condition in the `while` statement is evaluated again (i.e. the code "loops" back to the start), and if the condition still evaluates to `True`, the block of code is executed again ... and so on: as long as the condition is `True`, the indented block of code will be executed, over and over again.

*   This example shows a more general property of `while` loops: you must ensure that the `while` loop will terminate, or you will have an **infinite loop**, which will theoretically run forever

*   That is, there must be either:
    
    *   some statement in the block of code which modifies an object in the loop's condition, bringing it a step closer to termination during each iteration (as we have in the example above); or
    
    *   an explicit means of short-circuiting the loop within the block of code, and a guarantee that this will eventually happen

*   The general form of the while statement is the following:

    while <condition>:
        <block of statements>

*   When iterating, it is very common to need to assign values to variables which depend on the previous value of the variable. A particularly common one:
    *   `i = i + 1`

*   Can be shortened to:
    *   `i += 1`

*   There are many more, as indicated below:
    *   You might be able to notice a pattern: any operator plus the equals sign is the operator.

**Operator**

**Description**

`*=`

`c *= 2` is the same as `c = c * 2`

`/=`

`c /= 2` is the same as `c = c / 2`

`+=`

`c += 2` is the same as `c = c + 2`

`-=`

`c -= 2` is the same as `c = c - 2`

`//=`

`c //= 2` is the same as `c = c // 2`

`%=`

`c %= 2` is the same as `c = c % 2`

`**=`

`c **= 2` is the same as `c = c**2`

*   As hinted earlier, there is an alternative for exiting `while` loops: a `break` statement in the body of the loop, which terminates the iteration at the point it is executed

*   When using `break`, you need to be certain the `break` statement will be reached. If it's inside an `if` block which is never entered, your loop will be as infinite as `while True:`

For Loops:
----------

*   There is another way to iterate called a `for` loop. This may be thought of as analogous to the English expression _for each_. For example, the below code says: _for each element of the list, print that element_:
    
        my_list = [1,2,3]
        
        for elem in my_list:
        
            print(elem)
    
        1
        2
        3
    

*   In general, a `for` loop iterates over all elements of a sequence:
    *   if a sequence has five elements, e.g., the `for` loop will iterate five times.

*   This is the main difference as compared to `while` loops: the number of iterations of a `for` loop is generally pre-defined by the number of elements in the iterable it is applied to.

*   This makes it safe from infinite loops (unless you modify the object you are iterating over in the body of the `for` loop)

*   The general form of the `for` statement is the following:
    
        for <loop variable> in <iterable>:
        
            <block of statements>
    

*   What is an **iterable**? Simply a thing which can be iterated through.

*   The **loop variable** is the variable we define which takes the value of each item in the iterable in turn.
    
    *   The loop variable follows the naming rules of regular variable names so can be named just about anything.
    
    *   You are advised to choose a meaningful name, like `item` or `element` or something related to the data you're looping through, such as `letter`.
    
    *   This helps improve the readability of your code.
    
    *   You're also advised not to use the same name as any other variable in your code because its value would be overwritten.
    
    *   The loop variable will remain even after the loop is finished.

*   The `range()` function generates sequences of numbers
    
    *   It works in a very similar way to slices: you can specify a start number, an end number and an optional step (defaulting to `1`) in the form `range(start, end, step)`.
    
    *   The function returns a series of numbers starting from the `start` number, proceeding every `step` numbers until **one before** `end` (again, much like slices). The `start` value is optional as well, in fact, and will default to 0.

*   If the loop variable is not used inside the loop body at all, it is prefixed with an underscore like `_i` above.

### Loops Summary:

We have introduced the concept of **iteration** and seen the two types of loops which are available for us in Python.

*   Repetitive code is hard to read, hard to change, and inefficient to store. Iteration provides a means to produce more scalable and adaptive repetition in our code.

*   `while` loops are similar to `if` statements: they evaluate a condition and execute a block of code if the result is `True`. `while` loops continue to repeat their block of code while the condition remains `True` after being retested.

*   `for` loops automate the process of keeping track of which item you're up to when iterating through a sequence. The loop body executes once for each item in the given iterable object, with a loop variable taking the value of the current item.

*   The `+=` operator is a shortcut to incrementing a value. `operand1 += operand2` is equivalent to `operand1 = operand1 + operand2`. [Recall](https://media.giphy.com/media/3gNoskWiAwLKbfcCpE/giphy.gif) that `=` can also be added to the , , `/`, `//`, `%` and `*` operators in the same way.

The structure of a `while` loop:

    while <condition>:
    
        <block of code>

`while` loops have the risk that they may not terminate if the condition never evaluates to `False`. To avoid this, there must be either:

*   Some statement in the block of code while modifies an object in the condition such as to bring the condition closer to being `False` at each loop iteration; or

*   The use of a `break` statement inside the loop body, which terminates the loop when it is reached. Care must be given to ensure that this `break` statement is reached eventually.

The structure of a `for` loop:

    for <loop variable> in <iterable>:
    
        <block of code>

*   The loop variable can be named anything the programmer wishes, following the same rules as regular variable names.

*   Iterables are objects which may be iterated over; the only iterables we have seen so far are sequences (and the `range()` function's output).

*   `for` loops are safe from infinite loops, since the amount of iterations is predetermined by the number of elements in the sequence being iterated through.

*   The `range()` function is especially useful in `for` loops, either for iterating over indices or just iterating a specific amount of times. It takes a start number, end number and optional step number in a similar fashion to slicing, and generates an iterable object with a series of numbers from start to end, counting each step.

### Loop Conversion Summary:

We have looked at the differences between `for` and `while` loops, and how we can translate between them.

*   Three characteristics of loop behaviour can be identified to help convert between `for` and `while`.
    
    1.  Initialisation of a loop variable.
    
    2.  Update of the loop variable.
    
    3.  Termination of the loop.

*   When converting between `for` and `while` loops, it's important to capture these three things so that you can write them into the loop. These are considered for the two equivalent loops below:
    
        count = 0
        
        for i in range(5):
        
            count += i
        
        print(count)
    
        count = 0
        
        i = 0
        
        while i < 5:
        
            count += i
        
            i += 1
        
        print(count)
    

**Element**

`**for**` **loop**

`**while**` **loop**

Loop variable initialisation

`i` is specified as the loop variable. `range(5)` begins with `0` so the first value of `i` will be `0`.

The line `i = 0` initialises the loop variable.

Loop variable update

`range(5)` counts every item in sequence. No alternate `step` value was given, so `i` is incremented by `1` each loop.

The line `i += 1` increments the loop variable at each iteration.

Loop termination

The last item in `range(5)` is `4` so the last iteration will be when `i` has the value `4`.

The condition `i < 5` indicates that the loop will not continue when `i` becomes `5`.

*   A key difference between our two types of loops is that while in a `while` loop you must write all three steps explicitly, the `for` structure handles them automatically based on the value of the sequence being iterated through.

*   When converting from `while` to `for`, think of how to "build" them into the structure of the loop. When converting to `while`, think about what the `for` loop is doing automatically and write that into explicit statements.

*   `for` loops are generally better for iterating through sequences, though `while` loops can be more expressive in some instances, especially if you don't know how many times you will need to iterate.

*   All `for` loops can be converted into `while` loops by simulating the loop variable's behaviour. Some `while` loops cannot be converted into `for` loops, if they use the condition in an interesting way.
