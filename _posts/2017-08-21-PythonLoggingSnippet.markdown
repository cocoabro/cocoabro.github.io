---
layout:     post
title:      "Python Logging"
subtitle:   "Import logging configuration for libraries and application dev"
date:       2017-08-21 04:50:35 PM
author:     "Rob"
---

# Getting Started

Here is a quick snippet of setting up logging, which is a very useful thing to have when writing Libraries. 

# Setting up logging

The docs for ```logging``` module are overwhelming, so to break this down a little easier, I wanted to give you a quick start example so that you can be on your way. 

If you're writing a library, do this:

``` python
import logging
logger = logging.getLogger('mylibrary')
logger.addHandler(logging.NullHandler())

def do_stuff():
   ...
   logger.debug('doing stuff')
```
If you're writing an application, start your `main` with this:

``` python
import logging
logging.basicConfig()
```

It's not much, but this is a fast way to get you the information you need! 

Any questions? Don't hesitate to write to me at rob@robmcelvenny.com or leave your comments in the disqus box below! 


git remote add origin https://cocoabro:|}{!#gb123X!#@github.com/cocoabro.github.io.git

