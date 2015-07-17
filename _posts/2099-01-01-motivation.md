---
layout: post
title: Motivation
cover: none.png
date:   2099-01-01 12:00:00
categories: posts
---

Motivation
---

The bosslady dumps a pile of papers on your desk and demands that you fiture out what's up with the (quarterly sales numbers, vehicle crash statistics, material stress values, or any data analysis).  What do you do?

Maybe you like spreadsheets.  They're ok for basic things, but if you've ever found yourself wondering how to do a `for` loop in a spreadsheet, you're doing it wrong.

![awful uncomplicated spreadsheet]({{ site.baseurl }}/images/spreadsheet.png)

"All in one" tools like [scilab](http://scilab.org) are an improvement.  Combining data analysis, visualization, and scripting together with a unified syntax allows attacking many problems.  Even if they are extensible, however, I've found that it takes a great deal of effort to coerce them into inevitable edge cases.  No suite can handle everything, so flexibility is a must for all but the most rote work (which should be automated !).

If you've evolved beyond the mouse (and learned to love the 50+ buttons already at your fingertips), you should be comfortable with [CLI](http://en.wikipedia.org/wiki/Command-line_interface) or "terminal" programs to help you.  Linux gurus can combine text files, piping, redirection, and the nearly limitless open source programs to quickly manipulate and visualize data all in a `bash` shell.  I actually did most of my graduate thesis in `awk`.

```awk
#! /usr/bin/awk
# Sloppy grad school code, reformatted
month = d[1]; day = d[2]; year = d[3]
BEGIN {lastt[""]=495739;lengl[""]=19;frontl=4;FS=",";g=0;a=7}

{n = $3/2;
if (n == 1 || n == 2){
    if ($8 > 0 && $8 != "N/A"){
        #split date field
        split($5,d,"/");
        split($6,aa,":");
        split(aa[3],b,"[[:space:]+]");
# etc etc
}}
```

This works reasonably well, but doesn't scale for me.  Discovering subtle trends demands forming careful, complex, statements.  Being a human being, I make mistakes.  The smallest typos and the most misguided logical errors live on in my `bash` history.  So really, I want to write my commands in a [proper text editor](http://vim.org) (even a [heretical one](http://gnu.org/software/emacs/) is fine) and paste them over to the shell.  The mouse scurries back into my workflow...

To cut down some of the complexity (and save typing), you might try an interactive scripting environment like [`ipython`](http://ipython.org).  For most data analysis projects, this has almost everything I need (or is [extensible](http://python.org/pypi/ctypes)).  But inevitably, I still need a text editor to clearly iterate my commands.  Copy-paste burdens me.

Copying and pasting text might not seem like a serious slowdown.  But it disrupts flow.  Your hand leaves the keyboard to struggle with imprecise clicking.  Your mind shifts from binary keys to an analog cursor.  And every time you pay the context switching toll.

You don't have to suffer a mental tax to connect your text editor to your command-line.  [`slimux`]({{ site.baseurl }}/{%post_url 2070-01-01-slimux %}) bridges the gap, using just a few keystrokes to transfer text to your favorite terminal.  But first, we need to setup a lightweight environment that `slimux` uses, [`tmux`]({{ site.baseurl }}/{% post_url 2080-01-01-tmux %}).

* Learn about [`ipython`]({{ site.baseurl }}/{% post_url 2090-01-01-ipython %}) and get a handle on basic data manipulation.
* Multiply your terminal power with [`tmux`]({{ site.baseurl }}/{% post_url 2080-01-01-tmux %}).
