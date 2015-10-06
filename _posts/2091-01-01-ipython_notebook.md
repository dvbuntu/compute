---
layout: post
title: IPython Notebook / Jupyter
cover: none.png
date:   2090-01-01 12:00:00
categories: posts
---


# Take a Trip to Jupyter

Jupyter is a web-interface to some computing kernel, typically python, with logically distinct blocks separated into "cells" from first at the top and last at the bottom.  The input to each cell can be MarkDown, code running in a kernel (python, shell, etc), or raw text.  For code cells, you can also "run" them in their given kernel, whish is persistent within a kernel type.  That is, all `python` cells execute in one IPython session.  Further, output, such as lines of text or graphics appear immediately below the input in the same cell.  And these full notebooks can be exported to a variety of formats for easy sharing.  It's a very flexible yet powerful (and not to mention, popular!) system.

![jupyter]({{ site.baseurl }}/images/jupyter.png)

This addresses some of the concerns with the `slimux` REPL.  Namely, code that you write appears literally on top of the output it produces.  If you've brought up many images, you odn't have to guess which is which.  Further, the built-in MarkDown support means you have more precision avaiable to document your code and analysis.  And anyone can translate it into cleanly formatted HTML or whatever.  Analysis and sharing are easier.

Some Jupyter Tutorials:
* 1
* 2
* 3

Out of the bost, however, Jupyter needs a few add-ons to maintain key `slimux` REPL features.  First, while you can edit text right in the cell in a browser, you lose *all* the advanced text editing powers of ViM or emacs.  To restore your powers, I recommend the [`notebook_input_mode`](https://github.com/dvbuntu/notebook_input_mode) extension.  Some people prefer [`ipython-vimception`](https://github.com/ivanov/ipython-vimception), but that may not work with the latest version of Jupyter.  Similar add-ons are available for emacs users.  Now powered up, you can freely cut lines from one cell and paste in another (movement between cells can follow ViM movement commands as well).  Another limitation of Jupyter is that it uses JSON to store notebooks.  There's nothing wrong with this, but it's not very human readable for someone with your notebook but no Jupyter.  With `slimux`, the code is the document, as readable as that gets.  To amend this, install [`notedown`](https://github.com/aaren/notedown) and save notebooks natively as MarkDown.  This isn't perfect; images are still in base64 with JSON wrapping, but at least the code and documentation are preserved.  Now anyone viewing your notebook can understand it, no matter what software they lack.  Jupyter is highly extensible, making iteasy to add these killer features to be a great REPL.

# `slimux` vs Jupyter Comparison

Fully operational, Jpyter is a worthy alternative to `slimux`.  `slimux` seems to have the edge in speed.  Results from the associated IPython session are as quick as the underlying python.  Jupyter, perhaps because it is a web service, suffers from some delay.  It's not much, but if it can't keep up with your thoughts and code, it's a bottleneck.  On flexibility, `slimux` also takes the prize; it can execute commands on any interactive terminal program.  But Jupyter is no slouch, it provides all the common kernels like IPython, R, shell, etc and regularly adds more.  Jupyter's biggest strength is placing results practically in-line with input.  *When physical distance equals logical distance, insight blooms*.  `slimux` only enables this to the extent that the most recent output and input code block (to be fair, the most relevant) are likely to be in adjacent panes, though graphics appear in separate windows.  Also, it's worth noting that Jupyter is more popular; available help and documentation is a valuable feature.  Both `slimux` and Jupyter are capable workflows.

Workflow choice, something so local to the individual, comes down to personal preferences and project needs.  If you must use some legacy terminal framework or demand top speed, `slimux` may be for you.  If you need to collaborate with others in a popular language doing more analysis than development, Jupyter may be wiser.  In both cases, the key is to choose or design an effective computing workflow.  Rather than using your forehead to pound nails, it is better to pick up a hammer.

# Setup
* ipython notebook
* notebook_input_mode
    * run `python install.py`, make sure it installs to jupyter extensions, like `.local/share/jupyter/nbextensions/notebook_input_mode/`
* notedown
    * `sudo pip install https://github.com/aaren/notedown/tarball/master`
    * add `c.NotebookApp.contents_manager_class = 'notedown.NotedownContentsManager'` to `~/.jupyter/jupyter_notebook_config.py` #or `~/.ipython/ipython_notebook_config.py`.

# Use
* jupyter-notebook to launch (in home dir)
* Set keymap with Edit -> ViM
* ViM controls to move between cells, `i` or `Enter` to start editing that cell
    * now in ViM mode, `i` to go insert, `C-c` to switch to normal, Esc to switch to notebook level vim (rather than cell)
* `C-Enter` to run cell
* `C-s` to save and checkpoint notebook

# Learn
* http://pandas.pydata.org/pandas-docs/stable/tutorials.html

# Comments
* I do actually have tab complete!  This was almost a deal breaker
* But no autocomplete from ViM, not surprising
* Markdown notebooks don't actually save state, as expected, you have to rerun whole thing.  Reasonable
* kinda annoying to have to scroll down to see the output constantly...if it automatically scrolled with output, that would be nice
* Maybe I should work through a similar tutorial in my old style...or write such a tutorial.  Hmm
* pandas is really cool!

Ipython
---

`python` is an easy-to-learn programming language that is often fast enough for computing purposes.  `ipython` is a helpful interactive environment in which to run `python` code.  There are [numerous](http://showmedo.com/videotutorials/series?name=CnluURUTV) [guides](https://ipython.org/ipython-doc/3/interactive/tutorial.html) [online](https://damontallen.github.io/IPython-quick-ref-sheets/) for learning how to use `ipython`.  But there's a few tips that help you bootstrap yourself into an expert.


Getting Help
---

`foo?` will show you the docstring for the object `foo`.  This can be a class, function, instance, or pretty much anything.  This works on built-ins, modules, and anything you define in the local interpreter.  It reports some basic information (type, arguments, etc) always, but the docstring of course requires there to be some actual docstring.  For a function, this is the triple-quoted string that occurs immediately after the `def` line.

```python
[2]> bin?
Type:        builtin_function_or_method
String form: <built-in function bin>
Namespace:   Python builtin
Docstring:
bin(number) -> string

Return the binary representation of an integer.

   >>> bin(2796202)
   '0b1010101010101010101010'

[3]> int?
Type:            type
String form:     <class 'int'>
Namespace:       Python builtin
Init definition: int(self, *args, **kwargs)
Docstring:
int(x=0) -> integer
int(x, base=10) -> integer

Convert a number or string to an integer, or return 0 if no arguments
are given.  If x is a number, return x.__int__().  For floating point
numbers, this truncates towards zero.

If x is not a number or if base is given, then x must be a string,
bytes, or bytearray instance representing an integer literal in the
given base.  The literal can be preceded by '+' or '-' and be surrounded
by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
Base 0 means to interpret the base from the string as an integer literal.
>>> int('0b100', base=0)
```

`foo??` takes this one step further.  Sometimes the docstring isn't enough; you need to peek inside the python source code for a function to see what it's literally doing.  For functions, classes, methods, etc, `foo??` will show you the actual source code for that object.  Note that especially for built-ins, many functions are defined in C rather than python.  For these, you won't see any additional code.  Intermediate wrappers like SWIG will often show you the wrapping code, typically not very helpful.

```python
# nothing suspicious about this function
[18]> def foo():
          '''Return 4.0'''
          return 3.9999999

# Looks like a simple docstring
[19]> foo?
Type:        function
String form: <function foo at 0x7f06c1ab3d90>
File:        /home/user/<ipython-input-18-9b3437de933e>
Definition:  foo()
Docstring:   Return 4.0
      
# A little dishonest
[22]> foo??
Type:        function
String form: <function foo at 0x7f06c1ab3d90>
File:        /home/user/<ipython-input-18-9b3437de933e>
Definition:  foo()
Source:
def foo():
    '''Return 4.0'''
    return 3.9999999
```

`foo.[tab]` or `dir(foo)` is another critical learning tool.  It tells you what methods and attributes come with `foo`.  For new classes or objects, this is a great way to glance at what features or functions are already available.  Often, you know a library has some feature, and this will tell you how its named.  If you're used to GUIs, this is like looking through the menu to see what buttons you can click.  Note that `dir(foo)` will show you so-called "private" methods, those that begin with `__` (two underscores, or "dunder" in python parlance).  I typically stick with tab completion as the private methods often only clutter the view.

```python
[36]> a = 4
[37]> a.
a.bit_length   a.denominator  a.imag         a.real         
a.conjugate    a.from_bytes   a.numerator    a.to_bytes     
[37]> dir(a)
 #    
['__abs__',
 '__add__',
 '__and__',
...
```

Of course, you'll find yourself needing to combine these learning tools!  Tab complete may reveal some interesting methods, then you can look at what they are using the question marks.  Or the docstring points to another class, and you then run `dir` on it to reveal how to access it.

Having these key techniques ready at your fingertips is amazingly efficient.  They don't tell you everything, but they do let you quickly scan through your options, learn new methods, and see exactly what's occurring.  This is all within the interpreter and totally textual.  No browser, graphics, or network connection required.  Just instant feedback

numpy
---

`numpy` is a suite of Python libraries for doing numerical computations in arrays.  An array is like a list, but specific to one data type.  In a traditional Python list, you can put arbitrary objects into a list, ex.

```python
foo = [4, 'abc', math.sin]
```

While the generality of a list is very convenient, the price is that manipulating lists is expensive.  Every time you do an operation, Python has to check what type of object is in that position.  This also makes storing and accessing lists expensive.

`numpy` solves this problem by making arrays like `C` or `fortran` arrays.  That is, they are really just chunks of memory with a specfic data type.  This means that they are fast, memory efficient, and can quickly be manipulated.  `numpy` fully takes advantage of this, offering a fully-featured linear algebra library (implemented in a compiled language) to do computations on big arrays.  It makes it easy to compute on a significant amount of data.

```python
# It's easy to specify multidimensional arrays!
a = np.zeros([2,3,4])
a
array([[[ 0., 0., 0., 0.],
        [ 0., 0., 0., 0.],
        [ 0., 0., 0., 0.],

       [[ 0., 0., 0., 0.],
        [ 0., 0., 0., 0.],
        [ 0., 0., 0., 0.]]])
```

`numpy` has built-in convenient default behavior with matrices.  You can do things like add scalars to all elements, do an element-wise multiply with two matrices, and of course matrix multiplication.

```python
# add a scalar to a matrix
a = np.zeros([2,3])
a += 5
a
array([[[ 5.,  5.,  5.,  5.],
        [ 5.,  5.,  5.,  5.],
        [ 5.,  5.,  5.,  5.]],

       [[ 5.,  5.,  5.,  5.],
       [ 5.,  5.,  5.,  5.],
       [ 5.,  5.,  5.,  5.]]])

# element-wise multiplication
b = np.array([[1,2],[3,4]])
c = np.array([[6,7],[8,9]])
b*c
array([[ 6, 14],
       [24, 36]])

# matrix multiplication
np.dot(b,c)
array([[22, 25],
       [50, 57]])
```

pylab
---

Knowing how to get help and do fast numeric computations is wonderful, but interactive computing really shines when you can *plot* data in revealing ways.  `pylab` is one module that allows for simple interactive plotting.  Let's try plotting a few points:

```python
import pylab as pl
import numpy as np

# make some random data
a = np.random.rand(10,5)

# make plots show up when we call them
pl.ion()

# Plot the first row as a line, value vs index
pl.plot(a[0])

# How about red circles instead?
pl.plot(a[1],'ro')

# Get some more information
pl.plot? # super helpful
```

![Simple line and scatter plot]({{ site.baseurl }}/images/ipython_plot1.png)

`pylab` has lots of great plotting routines, but I want to highlight one other one in addition to the scatter plot.  `pylab` can also create heat maps.  That is, if you have a 2D array, imagine coloring each element based on its value.  Higher values might be more red and smaller values might be more blue.  This is often an excellent way to compare several rows of data or sense overall patterns.  I use heat maps almost every time I do data analysis.

```python
# Try this one simple command to make heat maps.  Fools hate it
pl.pcolor(a)

# Of course, lots of helpful options
pl.pcolor?
```

![heat plot]({{ site.baseurl }}/images/ipython_plot2.png)

These are the key `python` tools for doing effective data analysis.  You will surely find more specific ones as you get into projects, but I've found these to be remarkably applicable and resilient.  As a core foundation, it's hard to beat.
