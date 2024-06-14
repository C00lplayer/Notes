Worksheet 14: File IO and CSV files
===================================

**Date:** April 28, 2024

**Subject:** COMP10001


Files:
------

*   Python data structures such as lists and dictionaries are stored in computer **memory** (called RAM, or Random Access Memory) _only while their Python program is running_. This means that they are all deleted once the program stops.

*   **Files** provide a means of persistent storage (i.e. storage that persists through time, including when a computer is switched on and off), which you will be able to access later, send to others, etc.

*   The ability to work with files is very important when dealing with larger datasets, in terms of reading data in from files and writing data back out to files. As such, file manipulation is often called "file input/output" or **file IO**. To process the data in a file, you have to perform the following steps:
    
    1.  Open the file;
    
    2.  Read data from a file or write data to a file;
    
    3.  Close the file.
    
    *   The following analogy might help: to process a document in a drawer, you have to first open the drawer, then process the document (i.e. read it), and finally close the drawer.

*   It is necessary to open a file before performing other operations like reading, writing or appending to a file. Python provides a built-in function `open()` to open a file, that takes the file name as an argument (in the form of a string), and returns a **file object**, which you can manipulate to read the actual content of the file:
    ```python
        file_object = open("quotes.txt")
    ```

*   `open()` takes an optional second argument in the form of a string, which can be used to stipulate the "mode" in which to open the file. By default (without the second argument) the mode is **read only**

*   In practice, you can stipulate read mode with an `"r"`, as in:
    ```python
        file_object = open("quotes.txt", "r")
    ```
    *   Which is identical in functionality to the first call.

*   The other two commonly-used modes are **write** (= `"w"` as a mode string) and **append** (= `"a"` as mode string).

*   With write mode, if the file of that name pre-existed, its original contents are deleted when we write to it. If it didn't pre-exist, it is created first, ready to be written to.

*   In append mode, if the file pre-existed, we leave the original content intact: anything written is added to the end of the file. If it didn't pre-exist, append works identically to write: the file is first created, ready to be written to.

*   Both the write and append modes can be combined with the read mode.

*   Having opened a file (skipping the "reading/writing" part for now) it is good to get into the habit of closing it when you have finished with it. This is done using the `.close()` method:
    ```python
        file_object = open("quotes.txt")
        file_object.close()
    ```

*   When you close a file, two things happen: (1) all data that has been written/appended to the file is "flushed" through to the file, and it is closed on the computer's file system; and then (2) the file object associated with the file can no longer be used to manipulate the file.

*   An alternative way to open a file, which implicitly closes it when you're done, is to use a `with` statement

*   An alternative way to open a file, which implicitly closes it when you're done, is to use a `with` statement. This looks similar to a loop or conditional statement in that it has a colon at the end of the line and requires code to be indented in a block below it.
    ```python
        with open('myfile.txt', 'w') as fp:
            print("File is open: read/write here")
        print("File is closed: no .close() needed!")
    ```

*   The `open()` function call goes after `with` and the file object's name is entered after the word `as`

*   To read the contents of a file once you have opened it, Python file objects provide a range of methods, the `.read()` method reads the entire content of the file object associated with that file and returns it as a `str`, as we see in the following program:
    ```python
        fp = open("quotes.txt")
        content = fp.read()
        fp.close()
        print(content)
    ```
    ```
        'Twas brillig, and the slithy toves, Did gyre and gimble in the wabe: All mimsy were the borogoves, And the mome raths outgrabe.
    ```
*   Another useful and commonly-used method for reading files is `.readlines()`, which returns an iterable object which allows us to iterate over the lines in the file.
    ```python
        fp = open("jabberwocky1.txt")
        lineno = 1
        for line in fp.readlines():
            print(f"{lineno}: {line}", end='')
            lineno += 1
        fp.close()
    ```
    ```
        1: 'Twas brillig, and the slithy toves
        2: Did gyre and gimble in the wabe:
        3: All mimsy were the borogoves,
        4: And the mome raths outgrabe.
    ```
    *   Note the use of the `end` keyword in each call to `print()`, to suppress the insertion of a newline character, as each line in the file is, by definition, terminated by a newline.

*   You can also iterate over the lines in the file by iterating directly over the file handle:
    ```python
        fp = open("jabberwocky2.txt")
        lineno = 1
        for line in fp:  # note no readlines()
            print(f"{lineno}: {line}", end='')
            lineno += 1
        fp.close()
    ```
    ```
        1: "Beware the Jabberwock, my son!
        2: The jaws that bite, the claws that catch!
        3: Beware the Jubjub bird, and shun
        4: The frumious Bandersnatch!"
    ```

*   There also exists a `.readline()` method, which reads just one line of text. File objects remember where in a file you're up to so you could run this multiple times:
    ```python
        fp = open("jabberwocky3.txt")
        line = fp.readline()
        print(line, end='')
        line = fp.readline()
        print(line, end='')
        fp.close()
    ```
        'Twas brillig, and the slithy toves
        Did gyre and gimble in the wabe:
    ```

*   There is a `'\n'` character at the end of every string read by `.readlines()`

*   Having opened the file, you can then use the `.write(text)` method over a file handle to write the string `text` to that file, or `.writelines(str_list)` to write the list of strings `str_list` to the file.

### **Files Summary:**

We've learned about files and how to work with them in Python. We have been using **text files** in this worksheet, as opposed to any of the (many) other file formats for storing different data.

*   A **File** is a linear sequence of data stored on some persistent storage media. When dealing with larger amounts of data, storage to files becomes more important.

*   File manipulation is commonly called **File IO**.

To process data in a file, three operations must be performed in order:

1.  The file must be opened;
    
    *   Files are opened using the `open(filename, mode)` function, which takes the filename as a string. The `mode` is optional and will default to `'r'` for reading. `'w'` for writing and `'a'` for appending are common modes.
    
    *   Opening a file with mode `'w'` will overwrite any text already in the file when it is written to. Using `'a'` will add to the end of the file instead. Both will create a new file if one of the specified name does not already exist.
    
    *   `open()` returns a **file object** which can be used to read and write.

2.  The file's contents must be read or written;
    
    *   The `.read()` method, called on a file object, reads all the data from that file and returns it as a string.
    
    *   The `.readline()` method, called on a file object, returns a single line of text as a string.
    
    *   The `.readlines()` method, called on a file object, returns an iterable object containing each line of text as a separate string element to be looped through. This is more efficient than `.read()`. Iterating through the file object directly behaves the same way as using `.readlines()`.
    
    *   The `.write(text)` method, called on a file object, writes `text` to that file.
    
    *   The `.writelines(str_list)` method, called on a file object, writes each string in list `str_list` as separate lines to the file.

3.  The file must be closed.
    
    *   The `.close()` method closes the file object it is called on. It is important to do this when you have finished using a file.
    
    *   The `with open() as <name>:` statement is a convenient way to open a file and assign the file object. The file can be accessed only within the block of code associated with it, and it is `.close()`d automatically on exiting the code block.

CSV Files:
----------

*   The Comma-Separated Values (**CSV**) data format is a well-known format for representing tabular data.

*   It is one of the most common formats for importing and exporting data between spreadsheets and databases.

*   Its name emanates from the fact that each field or value in the data file is separated by a comma By convention,

*   CSV files have `.csv` at the end of their name (though it is not strictly required). Here is an example CSV file containing patient records:
    ```
        Patient ID,Name,Date admitted,Contact number
        126780,Alex McLeod,20/02/08,93761837
        126781,Cynthia Roberts,20/02/08,98557624
    ```

*   Each line in the data is called a **row** or a **record**.

*   The values in each column (called **field values**) are separated by a comma.

*   The first row is generally a header row, which describes the number and order of the field values in the data, along with a textual description of each.

*   For example, the above data has four fields, in order: `Patient ID`, `Name`, `Date admitted`, and `Contact number`.

*   Therefore, the last record corresponds to the patient with ID `126781`, name `Cynthia Roberts`, and so on.

*   The simplest way to iterate through the rows in a CSV file is with the `csv.reader()` function.

*   It takes an open file containing CSV data as its argument, and returns a special object called a **CSV reader**.

*   The `reader` object is a bit like `.readlines()` for iterating through files in that each row corresponds to a line in the CSV file, but in addition it automatically splits lines into a list of strings.

*   As part of this, it has the ability to determine whether a comma is a delimiter or part of the text within a field

*   For example: The following is an example CSV file named `"vic_visitors.csv"` that stores the number of visitors to regions in Victoria during 2004 and 2007 
    ```
        vic_visitors.csv
        Victoria's Regions,2004,2005,2006,2007
        Gippsland,63354,47083,51517,54872
        Goldfields,42625,36358,30358,36486
        Grampians,64092,41773,29102,38058
        Great Ocean Road,185456,153925,150268,167458
        Melbourne,1236417,1263118,1357800,1377291
    ```
    
    *   Let's first print the contents of the CSV file:
        ```python
            import csv
            
            visitors = open("vic_visitors.csv")
            
            for line in csv.reader(visitors):
            
                print(line)
            
            visitors.close()
        ```
        ```
            ["Victoria's Regions", '2004', '2005', '2006', '2007']
            ['Gippsland', '63354', '47083', '51517', '54872']
            ['Goldfields', '42625', '36358', '30358', '36486']
            ['Grampians', '64092', '41773', '29102', '38058']
            ['Great Ocean Road', '185456', '153925', '150268', '167458']
            ['Melbourne', '1236417', '1263118', '1357800', '1377291']
        ```

*   The first row of a CSV file is often a header. It is called the **header row** and provides a textual label for each column of the file.

*   If you wanted to retrieve the header, you could use the `next()` function, which causes the iterable to return its first element, and iterate onto the next row of data.

*   Initially, no row has been processed, so the first call of `next()` will simply return the header as in the following example:
    ```python
        import csv
        visitors = open("vic_visitors.csv")
        data = csv.reader(visitors)
        print(next(data))
        print(next(data))
        visitors.close()
    ```
    ```
        ["Victoria's Regions", '2004', '2005', '2006', '2007']
        ['Gippsland', '63354', '47083', '51517', '54872'
    ```

*   One issue with `csv.reader()` is that you have to hard-code which column is which by its column index, or save the header row as a list and double-check which row is which via the labels in list.

*   For CSV files with header rows, a more convenient and direct way of accessing the individual elements within a row is via `csv.DictReader()`, whereby each row is returned as a dictionary rather than a list, and a value can be referenced directly by its column label (assuming each column is uniquely labelled)

*   Consider the follow example involving the monthly rainfall measurements for the different state and territory capitals in a given year:
    ```python
        city_rainfall.csv
        city,Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec
        
        Melbourne,32.8,24.6,42.2,23,38.8,46.8,62.6,15,18.6,17.4,66.2,71.2
        
        Brisbane,184.4,216.8,20.6,3.2,39,112.6,1,91.2,32.4,55.2,61.8,79.2
        
        Darwin,515.2,670,689.8,18,18.8,4.2,0,0.4,43.6,13.2,143.2,247.8
        
        Perth,0,47.6,6.2,76.4,61.4,60,179.4,130.8,100.6,42.4,5.2,18
        
        Adelaide,9,3,24.6,82.4,45,64.8,65.8,25.8,24,25.2,29.6,37.6
        
        Canberra,43.8,64.6,36.6,27.8,41.6,92.8,18.8,11.6,14.6,22.6,94,101
        
        Hobart,2.8,64.8,24.2,26.2,31.2,29.6,36.8,59,62.8,44,7,83.4
        
        Sydney,57,258.4,65.4,179.6,9.8,510.6,67.2,152.2,41.2,27,170,123.2
    ```
    *   If we wanted to calculate the average monthly rainfall over the winter months in each case, we could do this as follows (remembering to convert numbers from a string into a number):
        ```python
            import csv
            cities = open("city_rainfall.csv")
            for row in csv.DictReader(cities):
                total = 0
                for month in ("Jun", "Jul", "Aug"):
                    total = total + float(row[month])
                print(f"{row['city']}: {total/3:.0f}")
            cities.close()
        ```
        ```
            Melbourne: 41
            Brisbane: 68
            Darwin: 2
            Perth: 123
            Adelaide: 52
            Canberra: 41
            Hobart: 42
            Sydney: 243
        ```

*   If you need to store your CSV data in a file, you can use the `csv.writer()` function. It takes a file object opened in write mode (`'w'`) and returns a special object called a CSV writer.

*   The CSV writer has methods for converting your lists of values to string lines. One such method is the `.writerows(data)` method. This method assumes that your data is represented as a nested list.

*   The following example writes a small 2D data structure to the CSV file `"2d-data.csv"`. It then prints out the contents of the file so that you can see how the 2D data is represented in a CSV file.
    ```python
        import csv
        
        data_2d = [[1, 2, 3], [4, 5, 6]]
        csv_file = open("2d-data.csv", "w")    
        writer = csv.writer(csv_file)
        writer.writerows(data_2d)
        csv_file.close()
        
        csv_file = open("2d-data.csv", "r")
        print(csv_file.read())
        csv_file.close()
    ```
    ```
        1,2,3
        4,5,6
    ```

### **CSV Summary:**

We've learned about CSV files and how they can be read and written with Python.

*   **CSV** (Comma-Separated Values) is a text-based data format which represents tabular data.

*   Each row represents a row or record of a spreadsheet. Commas separate individual values within each row.

*   The first row of a CSV file is generally a header row, which names what each column stores. The `next()` function is useful for advancing past the header when reading a csv file.
    ```
        example.csv
        header,row
        
        value,value
        
        value,value
    ```

*   The `csv` library provides methods for processing CSV files. It is more reliable than using `.readlines()` and `.split(',')`.

*   The `csv.reader(fp)` method takes a file object as an argument and returns a **csv reader object**, which can be iterated through to give each row of the CSV as a list of strings. The csv reader object splits each row its individual cells.

*   Converting a `csv.reader` object into a `list` converts that CSV file into a two-dimensional data representation, where a list of lists represents the rows and columns of the CSV file.
    ```python
        from csv import reader
        
        with open('example.csv', 'r') as fp:
        
            my_reader = reader(fp)
        
            print(list(my_reader))
    ```
    ```
        [['header', 'row'], ['value', 'value'], ['value', 'value']]
    ```

*   The `csv.DictReader(fp)` method takes a file object in a similar manner to `csv.reader()`, but instead returns a list of dictionaries for each row. Each dictionary has keys corresponding to the header labels and values corresponding to the values of that row in the CSV file.

*   The `csv.writer()` method takes a file object as an argument and returns a csv writer object.

*   The csv writer object has a `.writerows(data)` method which expects a two-dimensional data representation as input, and writes that data to the file in CSV format.

*   `.writerow(data)` takes a list and writes a single CSV row.
