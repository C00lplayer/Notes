Worksheet 18: Recursion
=======================

**Date:** May 20, 2024

**Subject:** COMP10001


Introduction to Recursion
-------------------------

*   Simply put, a recursive function is a function that calls itself.

*   A recursive function is made up of two parts:
    
    1.  The base case: This is the simplest version of the problem and where the function stops calling itself; in our student counting problem, this occurred when there was no other student left to ask.
    
    2.  The recursive case: This is where the function calls itself, and in doing so, it breaks the problem down into a smaller version of the problem; in our student counting problem, this was the case of there still being students left to ask the question of.

*   Say we want to calculate the sum of all the elements in a list which has an unknown number of nested lists. For example the sum of  `[1, [11, 42, [8, 1], 4, [22, 21]]]`  is 1+11+42+8+1+4+22+21=110.

*   The simplest version of this problem — i.e. **the base case** — is if you are given a list without any nested lists as input. Here’s what a simple solution would look like:
    ```python
        def nested_sum(my_list):
            sum = 0
            for elem in my_list:
                sum += elem
            return sum
    ```
        
    

*   Now let’s try to solve the original harder problem, the harder problem says that some of the elements in the list can be lists themselves, whereas with our simple solution we have assumed that all the elements will be numbers. Since we already know how to calculate the sum of a list of integers and floats, all we need to do is tweak our function to check whether or not the element we’re looking at is a list.
    ```python
        def nested_sum(my_list):
            sum = 0
            for elem in my_list:
                if type(elem) is list:
                    sum += nested_sum(elem)
                else:
                    sum += elem
            return sum
    ```

**Variables:**
--------------

*   You can think of a recursive function with a single recursive call as a stick (that's actually the technical term!) as you can see below.

*   This function processes a list by dealing with the first item, then making a recursive call to handle the rest of the list. You can see this in how at each stage, a number is extracted and the rest of the list is passed down to the next stage.
    
    [![]((https://file.notion.so/f/f/2a465c33-90bb-4d3f-af43-a6c939ce00ae/870a227a-a30a-4be7-853a-9c83c96dd1d1/Untitled.png?id=cc7dd8fc-7ba5-483e-9b01-db11a0676844&table=block&spaceId=2a465c33-90bb-4d3f-af43-a6c939ce00ae&expirationTimestamp=1718496000000&signature=FQWWbU5TXvRXFnIYKykEkv4I0wOEouVhYuf-e_-u7P8&downloadName=Untitled.png))
    

*   A recursive function with two recursive calls is like a tree (yes, again this is the technical term). Each function call recurses on the left half of the tree and then on the right half of the tree. If there's only one element, it will process that element. You can see the order of this below.
    
    [![](Worksheet%2018%20Recursion%20c516a1b0ec4942c78166750d12372793/Untitled%201.png)](Worksheet%2018%20Recursion%20c516a1b0ec4942c78166750d12372793/Untitled%201.png)
    

*   Which one is better? The stick looks shorter than the tree but for larger inputs, the tree becomes more and more efficient. In fact, trees are an important concept in Algorithms, and one you're sure to learn plenty about if you continue your studies in Computing.

### Summary:

*   Both iteration (while and for loops) and recursion do something similar i.e. solve a complicated task one piece at a time and combine the results:

|**Recursion**|**Iteration**|
|-------------|-------------|
|Breaks larger jobs into smaller jobs until they are basic enough to solve trivially, and then combine the results of all the smaller jobs|Focuses on repeating a single task until the job is done|
|More expensive for the computer to do (usually)|Cheaper for the computer (usually)|
|Can provide an intuitive solution for some problems|Can't be used to solve some problems because you need to know how deeply nested the lists are ahead of time, to know how many nested loops to use.|
|Some data structures are easier to explore using recursion (e.g. trees)|Some data structures are easier to explore using iteration (e.g. lists)|

*   So when should you use recursion? It really depends on the problem. If it’s impossible to know how many loops you’ll need to use, recursion is usually a safer bet. If you still can't quite grasp how recursion works, don’t worry! It’s not something you’re expected to have mastery over at this stage, and is more of a stretch than core topic for this subject.

*   In this worksheet, we've learned what recursion means and how to write recursive functions.

*   A recursive function is a function which calls itself.

*   Recursion can be an alternative to iteration, in that it provides a means of repetition. Often recursion is more computationally expensive than iteration, but in some cases a recursive solution is the only way a problem can be solved.

*   The two parts which each recursive function must have are:
    
    *   A base case. This is where the function stops calling itself and returns a calculated result.
    
    *   A recursive case. This is where the function calls itself recursively.

*   A recursive function must move towards its base case each time it recurses or else it may recurse infinitely, similar to how while loops must move towards termination in each iteration.

*   You can keep track of state between recursive function calls by passing arguments between function calls

*   Recursive functions execute in a stick-like pattern with one recursive call, but in a more efficient tree-like pattern with multiple recursive calls in a given function.  
    Recursion isn’t as bad as it seems!
