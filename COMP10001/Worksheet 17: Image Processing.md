Worksheet 17: Image Processing
==============================

**Date:** April 30, 2024

**Subject:** COMP10001


Pillow Tools:
-------------

*   The Python Image Library (PIL) is a Python package that provides tools for creating and manipulating digital images of a wide variety of formats

*   In particular, we will mainly use the `Image` submodule of the `PIL` module (the Python name of the Pillow library is the module `PIL`)

*   Pillow allows us to open image files using the `open()` function, and to create new images using `new()` function.

*   If you `import PIL.Image as pim`, these functions can be called in your program as follows:
    
    *   `pim.open(filename)` opens an image file called `filename` (a _string_). The file should be in the same folder as your Python program is running from (on Grok, this means it should be next to your program file in the editor window).
    
    *   `pim.new(mode, size, bg_colour)` creates a new blank image with colour-mode `mode` and dimensions `size`. The optional third argument `bg_colour` (background colour) will determine the starting colour of the image's pixels.

*   The return value of both of these functions is an object of a new data type called `Image`.
    *   This is a type defined for us by Pillow (not a built-in type like `int` or `str`) and stores an image, as you may expect.

>[!Note]
>Remember how when working with text files, we had to `.close()` a file when we were finished with it? PIL is smart in that it will automatically close any image files it opens. If you want to explicitly close a file, you can still run the `.close()` method but it's not strictly necessary.

*   Pillow uses strings to represent image colour modes. Here are some we will use:
    
    *   `"1"` for black and white images
    
    *   `"L"` for greyscale images
    
    *   `"RGB"` for RGB (Red, Green, Blue) colour images

*   We can also find these strings when we check the mode of an image. Say we have an `Image` object held in a variable called `my_image` , then the expression `my_image.mode` will evaluate to the string representing the mode of this image.

*   An image is a 2-dimensional grid of pixels.

*   This grid has a **width** (the number of columns) and a **height** (the number of rows).
    *   The width and height of an image's grid are referred to as its dimensions, and together they tells us the image's **size**.

*   When we create a new image using `pim.new()`, we must specify its size as the second argument. For example, to create a 200 (width) by 300 (height) RGB image, we could use the following program:
    ```python
        import PIL.Image as pim
        
        my_image = pim.new("RGB", (200, 300))
    ```
    *   `size` is a single parameter which takes both width and height together in the form of a 2-tuple.

*   When we load an image, we may want to know its size. We can get this from the `Image` object using a few more of its fields.
    
    *   There's a `size` field which is  `my_image.size` which is a tuple representation of the size (like the one we pass to `pim.new()`).
    
    *   We can get each dimension individually, too: there's also a `width` field and a `height` field. So `my_image.width` would evaluate to `200` in the above example program, and  `my_image.height`  would evaluate to `300`.

*   We can get the colour value of any pixel in an `Image` object's grid by using a special method called `.getpixel()`.

*   `getpixel(address)` takes one argument: the address of the pixel. Pixel addresses are another example of a 2-tuple.
    
    *   The first number in the tuple is the column number or x-coordinate, and the second number is the row number or y-coordinate.
    
    *   Note that is the opposite order of when we were using nested lists to represent images in Worksheet 13. Coordinate numbers start from 0, so the top-left pixel of an image has address `(0,0)`

*   The colour value it returns will be as follows:
    
    *   For a black and white image (mode `"1"`), it will be `0` for black, or `1` for white.
    
    *   For a greyscale image (mode `"L"`), it will be a number between 0 and 255 (inclusive): `0` for black, `255` for white.
    
    *   For an RGB image (mode `"RGB"`), it will be a **3-tuple** of values.
        
        *   This tuple will contain three values, all between 0 and 255 (inclusive).
        
        *   The first value will be the amount of red in the pixel
        
        *   The second the amount of green
        
        *   Then third the amount of blue.
        
        *   In each **channel**, 0 represents absence of that colour and 255 represents the full amount of that colour.

*   To see an example of this, have a look at this example program:
    ```python
        import PIL.Image as pim
        image = pim.new("L", (2, 2))
        top_left = image.getpixel((0, 0))
        top_right = image.getpixel((1, 0))
        bot_left = image.getpixel((0, 1))
        bot_right = image.getpixel((1, 1))
        print(top_left, top_right)
        print(bot_left, bot_right)
    ```
    ```
        0 0
        0 0
    ```
    *   This program creates a small (2 by 2) greyscale image, and uses the `.getpixel()` method to find the colour values of the four pixels in the image. It then prints these values out in a grid.
    
    *   The returned colour values are all 0, meaning the pixels are black.
    
    *   This is the default colour of all new greyscale images, unless we pass a different colour value as an optional third argument in the call to `pim.new()`.

*   The `.getpixel()` method returns the colour value of a pixel given its address, but doesn't do anything to the colour value. If we want to put a colour value in a pixel, we'll need to use another method of the `Image` object: `.putpixel()`.

*   `.putpixel(address, colour)` takes two arguments:
    
    *   Like `.getpixel()`, it needs a pixel address in the form of a 2-tuple.
    
    *   As a second argument, it will take the new colour value for the pixel. Depending on the mode, this will be:
        
        *   0 or 1 for a black and white image
        
        *   a number between 0 and 255 for a greyscale image
        
        *   a 3-tuple of numbers between 0 and 255 for an RGB image (the first is red, the second is green, the third is blue).

*   Like `.getpixel()`, `.putpixel()` is a _method_ of an `Image` object. That means we need a particular `Image` object in order to call it.

*   For example, to set the pixel at address `(10, 20)` of an RGB image in a variable called `my_image` to red value 255, green value 127 and blue value 63, we'd use the following call:
    ```python
        my_image.putpixel((10, 20), (255, 127, 63))
    ```

*   One final useful `Image` object method is `.save()`. 

*   `.save(filename)` takes a single argument: a string filename like the ones we give to  `pim.open()`. It does what you would expect: saves the image to a file with that name.
    ```python
        my_image.save('my_image.png')
    ```

*   Importantly, the filename should have an extension (like `.png`) so that Pillow can figure out how to format the file it creates.
    *   Can also be JPEG, GIF, or SVG

### **Pillow tools Summary:**

We've learned about the Pillow library and how to manipulate images in Python.

*   Pillow is based on the Python Image Library (PIL). It is a non-standard library which provides tools for creating and manipulating images.

*   Pillow is imported by the statement `import PIL.Image` or `from PIL import Image`

*   `pim.open(filename)` opens an image file which must already exist, called `filename`. It returns a pillow `Image` object.

*   `pim.new(mode, size, bg_colour)` creates a new blank `Image` object with colour-mode `mode` and dimensions `size`. The optional third argument `bg_colour` (background colour) will determine the starting colour of the image's pixels.
    
    *   `mode` should be `"1"` for black and white images, `"L"` for greyscale images, or `"RGB"` for RGB (Red, Green, Blue) colour images.
    
    *   `size` is specified by a 2-tuple containing the width and the height of the image in pixels.

*   The `.getpixel(address)` method, applied to an `Image` object, takes the address of a pixel as a 2-tuple and returns the colour of that pixel.
    
    *   For `mode "1"`, the colour will be 0 for black, or 1 for white. For `mode "L"`, it will be a number between 0 and 255 (inclusive): 0 for black, 255 for white. For `mode "RGB"`, it will be a 3-tuple of numbers between 0 and 255 (inclusive), specifying for the amount of red, green, and blue, respectively.
    
    *   Like with sequences, trying to access a pixel which doesn't exist will cause an `IndexError`.

*   The `.putpixel(address, colour)` method, applied to an `Image` object, takes the address of a pixel as a 2-tuple, and a new colour value for that pixel. It will save the new colour to that pixel, without returning anything.

*   The `.save(filename)` method, applied to an `Image` object, takes a string filename, ending with an extension such as `.png`, and saves the image to a file with that name.

**Images and loops:**
---------------------

*   We'll need to master some techniques for managing large grids of pixels.

*   Fortunately, we have a programming tool perfect for handling repetitive tasks: the `for` loop. Almost every image program you write will involve multiple `for` loops.

*   Here's an example of an image program that uses `for` loops to create a 32 by 24 image of a black cross on a white background (note the third argument in the call to `pim.new()`). Study the program to understand how the loop variable is used to determine which pixel addresses to colour in:
    ```python
        import PIL.Image as pim
        my_image = pim.new("1", (32, 24), 1)
        for i in range(32):
            my_image.putpixel((i, 11), 0)
            my_image.putpixel((i, 12), 0)
        for i in range(24):
            my_image.putpixel((11, i), 0)
            my_image.putpixel((12, i), 0)
    ```

*   The resulting image (if we saved it) would look something like this:
    
    [![](https://groklearning-cdn.com/modules/oQuQHnJwM8Pat3aXQ6NHtS/cross.grid.png)](https://groklearning-cdn.com/modules/oQuQHnJwM8Pat3aXQ6NHtS/cross.grid.png)
    

*   `for` loops are good for drawing lines on images. But, like colouring a drawing with a thin pencil, it takes many lines to fill in a shape with colour. If we had to write a separate loop for each line, we wouldn't be that much better than when we were colouring in pixels individually.

*   But, of course, we can even use `for` loops to avoid repeating `for` loops! Filling in an area of an image is the perfect place to use a pair of _nested_ `for` loops. The inner `for` loop can draw lines and the outer `for` loop can repeat that line-drawing process over the whole image!
    *   Here's an example program that starts with a white image but fills it entirely black:
```python
    import PIL.Image as pim
    my_image = pim.new("1", (32, 24), 1)
    for x in range(32):
        for y in range(24):
            my_image.putpixel((x, y), 0)
```
*   In particular, note the naming of the loop variables: `x` for the outer loop variable (which ranges from 0 to 31, the exact range of the image's column numbers) and `y` for the inner loop variable (it ranges from 0 to 23, the exact range of the image's row numbers).

Effects and transformations
---------------------------

*   As a simple first example, let's say we have a greyscale image and want to darken it. The lightness of a pixel in a greyscale image is controlled by its colour value: the higher the colour value (the closer to 255, which indicates white), the brighter that pixel.

*   To achieve a darkening effect, it should do the trick if we somehow reduce the colour of each pixel. Let's say we decide to try reducing each pixel's colour value by a factor of 2 for the darkened image. Then we can set the colour value of the corresponding pixel in the new image to half that of the pixel in the original image. We need to make sure that the result is an integer so that it is a valid colour value: integer division helps with this.
    
    *   Here's some code that demonstrates this technique:
        ```python
            import PIL.Image as pim
            original = pim.open("input.png")
            darkened = pim.new("L", original.size)
            for x in range(original.width):
                for y in range(original.height):
                    old_colour = original.getpixel((x, y))
                    new_colour = old_colour // 2
                    darkened.putpixel((x, y), new_colour)
            darkened.save('output.png')
        ```
    
    *   The effect will be as follows:
        
        [![](https://groklearning-cdn.com/modules/6rjoPetDWczjREA799gnpD/spaceman.png)](https://groklearning-cdn.com/modules/6rjoPetDWczjREA799gnpD/spaceman.png)
        
        input.png
        
        [![](https://groklearning-cdn.com/modules/AwpNud8RLtf7BBFUrPyriG/spaceman-dark.png)](https://groklearning-cdn.com/modules/AwpNud8RLtf7BBFUrPyriG/spaceman-dark.png)
        
        output.png
        

*   RGB images are a little trickier to work with, only because each pixel's colour value is actually _three_ values, inside a **tuple**

*   But one question you will run into as soon as you try to write an RGB image program is how to get individual colour values out of the tuple you get back from `.getpixel()`. One method of 'unpacking' tuples is shown in the following program
    ```python
        import PIL.Image as pim
        rgb_image = pim.new("RGB", (10, 10), (199, 36, 255))
        colour_value = rgb_image.getpixel((0, 0))
        print("Colour value:", colour_value)
        r, g, b = rgb_image.getpixel((0, 0))
        print("Red:  ", r)
        print("Green:", g)
        print("Blue: ", b)
    ```
    ```
        Colour value: (199, 36, 255)
        Red:   199
        Green: 36
        Blue:  255
    ```

*   We have seen examples where each pixel in an output image has a colour value based only on the colour value of the corresponding pixel in an input image. However, it's also possible to apply image transformations (reflections, rotations, and more).

*   For example, let's say we wanted a new image that was a horizontal reflection of an existing image (a reflection in the vertical axis). We could view this as each pixel of the new image being based on the horizontally opposite pixel in the original image:
    
    [![](https://groklearning-cdn.com/modules/7dvLfDNpNL7pZx83oTHBHB/reflect-source.png)](https://groklearning-cdn.com/modules/7dvLfDNpNL7pZx83oTHBHB/reflect-source.png)
    
    *   Pixels in the new image (right) correspond to other pixels in the original image (left)

*   We'll call the pixel from our original image the 'source' pixel, and the corresponding pixel in the reflected image the 'destination' pixel. For a given destination pixel at address (x,y), the source pixel will have the same row number (y) but a different column number (x). Can we calculate the column number? Yes, the source pixel should be as far from the right edge of the original image as the destination pixel is from the left edge of the reflected image:

[![](https://groklearning-cdn.com/modules/f3ZgdbyGz7FuJLmmPLpdnk/reflect-x.png)](https://groklearning-cdn.com/modules/f3ZgdbyGz7FuJLmmPLpdnk/reflect-x.png)

*   The corresponding column number can be calculated with the formula:

      $width−1−x$
    
    *   Where width is the width of both images in pixels. (See note below for an explanation of the −1.)

*   The following program then performs this transformation:
    ```python
        import PIL.Image as pim
        original = pim.open("input.png")
        reflected = pim.new(original.mode, original.size)
        for x in range(reflected.width):
            for y in range(reflected.height):
                source_pixel = (reflected.width - 1 - x, y)
                colour_value = original.getpixel(source_pixel)
                reflected.putpixel((x, y), colour_value)
    ```
    *   In particular, notice the flow inside the inner loop: calculate the address of the source pixel, get the source pixel's colour value, set the destination pixel's colour value.
    
    *   This pattern (and slight variations) will help us tackle more complex transformations.

>[!Important]
>We use `reflected.width - 1 - x` as the x-coordinate of the source pixel in the above program. Why isn't it `reflected.width - x`?
>If you try removing the `- 1`, you will see an error. This is because when `x` is `0` (the first time round the loop), we'll try to access the pixel in column number `reflected.width - 0` which is just `reflected.width` which doesn't exist.
>If the image's width is, say, 100, then the right-most column is numbered 99: remember, we are counting from 0 so column 100 doesn't exist! This explains the error. We need that `- 1` to make sure the column number comes out just right.
>This type of error is sometimes called an 'off-by-one' error or a 'fencepost' error, because these tricky boundary cases show up all over programming problems.

### **Image Transformations Summary:**

We've seen how loops can be used with images and how effects and transformations can be applied to images.

*   `for` loops are helpful for colouring rows or columns of an image. Nested loops can be used to colour multiple rows or columns.

*   Image manipulation is typically done by creating a new image which is coloured with an alteration of the original image.

*   An image can be darkened by reducing the colour value of each pixel by some amount. Raising the colour value would brighten the image.

*   Unpacking is a useful way to extract the three _RGB_ values from a colour pixel's tuple.
    ```python
        r, g, b = rgb_image.getpixel((0, 0))
    ```

*   Transformations such as rotations and flips can be applied by assigning source pixels from the original image to different destination pixels in a transformed image.

*   The dimension of an image can be grown (or shrunk) in either dimension by mapping one (or many) source pixel(s) to many (or one) destination pixel(s).
