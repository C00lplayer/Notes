Worksheet 3: Conditionals /\* cspell:disable-file \*/ /\* webkit printing magic: print all background colors \*/ html { -webkit-print-color-adjust: exact; } \* { box-sizing: border-box; -webkit-print-color-adjust: exact; } html, body { margin: 0; padding: 0; } @media only screen { body { margin: 2em auto; max-width: 900px; color: rgb(55, 53, 47); } } body { line-height: 1.5; white-space: pre-wrap; } a, a.visited { color: inherit; text-decoration: underline; } .pdf-relative-link-path { font-size: 80%; color: #444; } h1, h2, h3 { letter-spacing: -0.01em; line-height: 1.2; font-weight: 600; margin-bottom: 0; } .page-title { font-size: 2.5rem; font-weight: 700; margin-top: 0; margin-bottom: 0.75em; } h1 { font-size: 1.875rem; margin-top: 1.875rem; } h2 { font-size: 1.5rem; margin-top: 1.5rem; } h3 { font-size: 1.25rem; margin-top: 1.25rem; } .source { border: 1px solid #ddd; border-radius: 3px; padding: 1.5em; word-break: break-all; } .callout { border-radius: 3px; padding: 1rem; } figure { margin: 1.25em 0; page-break-inside: avoid; } figcaption { opacity: 0.5; font-size: 85%; margin-top: 0.5em; } mark { background-color: transparent; } .indented { padding-left: 1.5em; } hr { background: transparent; display: block; width: 100%; height: 1px; visibility: visible; border: none; border-bottom: 1px solid rgba(55, 53, 47, 0.09); } img { max-width: 100%; } @media only print { img { max-height: 100vh; object-fit: contain; } } @page { margin: 1in; } .collection-content { font-size: 0.875rem; } .column-list { display: flex; justify-content: space-between; } .column { padding: 0 1em; } .column:first-child { padding-left: 0; } .column:last-child { padding-right: 0; } .table\_of\_contents-item { display: block; font-size: 0.875rem; line-height: 1.3; padding: 0.125rem; } .table\_of\_contents-indent-1 { margin-left: 1.5rem; } .table\_of\_contents-indent-2 { margin-left: 3rem; } .table\_of\_contents-indent-3 { margin-left: 4.5rem; } .table\_of\_contents-link { text-decoration: none; opacity: 0.7; border-bottom: 1px solid rgba(55, 53, 47, 0.18); } table, th, td { border: 1px solid rgba(55, 53, 47, 0.09); border-collapse: collapse; } table { border-left: none; border-right: none; } th, td { font-weight: normal; padding: 0.25em 0.5em; line-height: 1.5; min-height: 1.5em; text-align: left; } th { color: rgba(55, 53, 47, 0.6); } ol, ul { margin: 0; margin-block-start: 0.6em; margin-block-end: 0.6em; } li > ol:first-child, li > ul:first-child { margin-block-start: 0.6em; } ul > li { list-style: disc; } ul.to-do-list { padding-inline-start: 0; } ul.to-do-list > li { list-style: none; } .to-do-children-checked { text-decoration: line-through; opacity: 0.375; } ul.toggle > li { list-style: none; } ul { padding-inline-start: 1.7em; } ul > li { padding-left: 0.1em; } ol { padding-inline-start: 1.6em; } ol > li { padding-left: 0.2em; } .mono ol { padding-inline-start: 2em; } .mono ol > li { text-indent: -0.4em; } .toggle { padding-inline-start: 0em; list-style-type: none; } /\* Indent toggle children \*/ .toggle > li > details { padding-left: 1.7em; } .toggle > li > details > summary { margin-left: -1.1em; } .selected-value { display: inline-block; padding: 0 0.5em; background: rgba(206, 205, 202, 0.5); border-radius: 3px; margin-right: 0.5em; margin-top: 0.3em; margin-bottom: 0.3em; white-space: nowrap; } .collection-title { display: inline-block; margin-right: 1em; } .page-description { margin-bottom: 2em; } .simple-table { margin-top: 1em; font-size: 0.875rem; empty-cells: show; } .simple-table td { height: 29px; min-width: 120px; } .simple-table th { height: 29px; min-width: 120px; } .simple-table-header-color { background: rgb(247, 246, 243); color: black; } .simple-table-header { font-weight: 500; } time { opacity: 0.5; } .icon { display: inline-block; max-width: 1.2em; max-height: 1.2em; text-decoration: none; vertical-align: text-bottom; margin-right: 0.5em; } img.icon { border-radius: 3px; } .user-icon { width: 1.5em; height: 1.5em; border-radius: 100%; margin-right: 0.5rem; } .user-icon-inner { font-size: 0.8em; } .text-icon { border: 1px solid #000; text-align: center; } .page-cover-image { display: block; object-fit: cover; width: 100%; max-height: 30vh; } .page-header-icon { font-size: 3rem; margin-bottom: 1rem; } .page-header-icon-with-cover { margin-top: -0.72em; margin-left: 0.07em; } .page-header-icon img { border-radius: 3px; } .link-to-page { margin: 1em 0; padding: 0; border: none; font-weight: 500; } p > .user { opacity: 0.5; } td > .user, td > time { white-space: nowrap; } input\[type="checkbox"\] { transform: scale(1.5); margin-right: 0.6em; vertical-align: middle; } p { margin-top: 0.5em; margin-bottom: 0.5em; } .image { border: none; margin: 1.5em 0; padding: 0; border-radius: 0; text-align: center; } .code, code { background: rgba(135, 131, 120, 0.15); border-radius: 3px; padding: 0.2em 0.4em; border-radius: 3px; font-size: 85%; tab-size: 2; } code { color: #eb5757; } .code { padding: 1.5em 1em; } .code-wrap { white-space: pre-wrap; word-break: break-all; } .code > code { background: none; padding: 0; font-size: 100%; color: inherit; } blockquote { font-size: 1.25em; margin: 1em 0; padding-left: 1em; border-left: 3px solid rgb(55, 53, 47); } .bookmark { text-decoration: none; max-height: 8em; padding: 0; display: flex; width: 100%; align-items: stretch; } .bookmark-title { font-size: 0.85em; overflow: hidden; text-overflow: ellipsis; height: 1.75em; white-space: nowrap; } .bookmark-text { display: flex; flex-direction: column; } .bookmark-info { flex: 4 1 180px; padding: 12px 14px 14px; display: flex; flex-direction: column; justify-content: space-between; } .bookmark-image { width: 33%; flex: 1 1 180px; display: block; position: relative; object-fit: cover; border-radius: 1px; } .bookmark-description { color: rgba(55, 53, 47, 0.6); font-size: 0.75em; overflow: hidden; max-height: 4.5em; word-break: break-word; } .bookmark-href { font-size: 0.75em; margin-top: 0.25em; } .sans { font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol"; } .code { font-family: "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace; } .serif { font-family: Lyon-Text, Georgia, ui-serif, serif; } .mono { font-family: iawriter-mono, Nitti, Menlo, Courier, monospace; } .pdf .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK JP'; } .pdf:lang(zh-CN) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK SC'; } .pdf:lang(zh-TW) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK TC'; } .pdf:lang(ko-KR) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK KR'; } .pdf .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP'; } .pdf:lang(zh-CN) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC'; } .pdf:lang(zh-TW) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC'; } .pdf:lang(ko-KR) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR'; } .pdf .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK JP'; } .pdf:lang(zh-CN) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK SC'; } .pdf:lang(zh-TW) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK TC'; } .pdf:lang(ko-KR) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK KR'; } .pdf .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP'; } .pdf:lang(zh-CN) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC'; } .pdf:lang(zh-TW) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC'; } .pdf:lang(ko-KR) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR'; } .highlight-default { color: rgba(55, 53, 47, 1); } .highlight-gray { color: rgba(120, 119, 116, 1); fill: rgba(120, 119, 116, 1); } .highlight-brown { color: rgba(159, 107, 83, 1); fill: rgba(159, 107, 83, 1); } .highlight-orange { color: rgba(217, 115, 13, 1); fill: rgba(217, 115, 13, 1); } .highlight-yellow { color: rgba(203, 145, 47, 1); fill: rgba(203, 145, 47, 1); } .highlight-teal { color: rgba(68, 131, 97, 1); fill: rgba(68, 131, 97, 1); } .highlight-blue { color: rgba(51, 126, 169, 1); fill: rgba(51, 126, 169, 1); } .highlight-purple { color: rgba(144, 101, 176, 1); fill: rgba(144, 101, 176, 1); } .highlight-pink { color: rgba(193, 76, 138, 1); fill: rgba(193, 76, 138, 1); } .highlight-red { color: rgba(212, 76, 71, 1); fill: rgba(212, 76, 71, 1); } .highlight-gray\_background { background: rgba(241, 241, 239, 1); } .highlight-brown\_background { background: rgba(244, 238, 238, 1); } .highlight-orange\_background { background: rgba(251, 236, 221, 1); } .highlight-yellow\_background { background: rgba(251, 243, 219, 1); } .highlight-teal\_background { background: rgba(237, 243, 236, 1); } .highlight-blue\_background { background: rgba(231, 243, 248, 1); } .highlight-purple\_background { background: rgba(244, 240, 247, 0.8); } .highlight-pink\_background { background: rgba(249, 238, 243, 0.8); } .highlight-red\_background { background: rgba(253, 235, 236, 1); } .block-color-default { color: inherit; fill: inherit; } .block-color-gray { color: rgba(120, 119, 116, 1); fill: rgba(120, 119, 116, 1); } .block-color-brown { color: rgba(159, 107, 83, 1); fill: rgba(159, 107, 83, 1); } .block-color-orange { color: rgba(217, 115, 13, 1); fill: rgba(217, 115, 13, 1); } .block-color-yellow { color: rgba(203, 145, 47, 1); fill: rgba(203, 145, 47, 1); } .block-color-teal { color: rgba(68, 131, 97, 1); fill: rgba(68, 131, 97, 1); } .block-color-blue { color: rgba(51, 126, 169, 1); fill: rgba(51, 126, 169, 1); } .block-color-purple { color: rgba(144, 101, 176, 1); fill: rgba(144, 101, 176, 1); } .block-color-pink { color: rgba(193, 76, 138, 1); fill: rgba(193, 76, 138, 1); } .block-color-red { color: rgba(212, 76, 71, 1); fill: rgba(212, 76, 71, 1); } .block-color-gray\_background { background: rgba(241, 241, 239, 1); } .block-color-brown\_background { background: rgba(244, 238, 238, 1); } .block-color-orange\_background { background: rgba(251, 236, 221, 1); } .block-color-yellow\_background { background: rgba(251, 243, 219, 1); } .block-color-teal\_background { background: rgba(237, 243, 236, 1); } .block-color-blue\_background { background: rgba(231, 243, 248, 1); } .block-color-purple\_background { background: rgba(244, 240, 247, 0.8); } .block-color-pink\_background { background: rgba(249, 238, 243, 0.8); } .block-color-red\_background { background: rgba(253, 235, 236, 1); } .select-value-color-uiBlue { background-color: rgba(35, 131, 226, .07); } .select-value-color-pink { background-color: rgba(245, 224, 233, 1); } .select-value-color-purple { background-color: rgba(232, 222, 238, 1); } .select-value-color-green { background-color: rgba(219, 237, 219, 1); } .select-value-color-gray { background-color: rgba(227, 226, 224, 1); } .select-value-color-transparentGray { background-color: rgba(227, 226, 224, 0); } .select-value-color-translucentGray { background-color: rgba(255, 255, 255, 0.0375); } .select-value-color-orange { background-color: rgba(250, 222, 201, 1); } .select-value-color-brown { background-color: rgba(238, 224, 218, 1); } .select-value-color-red { background-color: rgba(255, 226, 221, 1); } .select-value-color-yellow { background-color: rgba(253, 236, 200, 1); } .select-value-color-blue { background-color: rgba(211, 229, 239, 1); } .select-value-color-pageGlass { background-color: undefined; } .select-value-color-washGlass { background-color: undefined; } .checkbox { display: inline-flex; vertical-align: text-bottom; width: 16; height: 16; background-size: 16px; margin-left: 2px; margin-right: 5px; } .checkbox-on { background-image: url("data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20width%3D%2216%22%20height%3D%2216%22%20fill%3D%22%2358A9D7%22%2F%3E%0A%3Cpath%20d%3D%22M6.71429%2012.2852L14%204.9995L12.7143%203.71436L6.71429%209.71378L3.28571%206.2831L2%207.57092L6.71429%2012.2852Z%22%20fill%3D%22white%22%2F%3E%0A%3C%2Fsvg%3E"); } .checkbox-off { background-image: url("data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20x%3D%220.75%22%20y%3D%220.75%22%20width%3D%2214.5%22%20height%3D%2214.5%22%20fill%3D%22white%22%20stroke%3D%22%2336352F%22%20stroke-width%3D%221.5%22%2F%3E%0A%3C%2Fsvg%3E"); }

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
