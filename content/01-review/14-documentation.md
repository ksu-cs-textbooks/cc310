---
title: "Documentation"
weight: 75
pre: "14. "
---
It is important both to easily grasp the design choice and the code structure of a project even long after it has been completed. The documentation process starts by commenting the code. Code comments are usually intended for software developers and aim at clarifying the code by giving details of how it works. They are usually performed using inline or multiple lines comments using the language syntax. 

## Single Line Comments

As we've seen before, we can add single-line comments to our Python programs using a hash symbol `#` before a line in our source file:

```python
# this is a comment
x = 5

# this is also a comment
b = True
```

## Docstrings

Finally, Python also includes a secondary type of comment that spans multiple lines, specifically for creating documentation. A docstring is usually the first line of text inside of a class or method definition, and is surrounded by three double quotes `"""` with one set of three on each end. 

These comments are specifically designed to provide information about classes and methods in our code. Here's a quick example using a simple class:

```python
class IntTuple:
  """ Represents a tuple containing two integer values
  
  This class is an adaptation of a class developed for Java
  that mimics the built-in tuples in Python
  
  Attributes
  ----------
  first : int
      the first element in the tuple
  second : int
      the second element in the tuple
  """
  
  def __init__(self, one, two):
    """ Initializes a new IntTuple object
    
    Parameters
    ----------
    one : int
        the first element in the new tuple
    two : int
        the second element in the new tuple
    """
    self.first = one
    self.second = two
```

Unfortunately, Python does not enforce a particular style for these docstrings, so there are many different formats used in practice. To learn more, we can consult the following references.

## References

* [Documenting Python Code](https://realpython.com/documenting-python-code/) from Real Python
* [Google Docstring Style Guide](https://github.com/google/styleguide/blob/gh-pages/pyguide.md#38-comments-and-docstrings)
* [reStructured Text](http://docutils.sourceforge.net/rst.html) - The format used in official Python libraries
