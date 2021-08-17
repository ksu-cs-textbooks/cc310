---
title: "Overloading"
weight: 10
pre: "2. "
---
{{% youtube AOtnZGIqsaQ %}}

Python allows us to specify default values for parameters in a function definition. In that way, if those parameters are not provided, the default value will be used instead. So, it may appear that there are multiple functions with the same name that accept a different number of parameters. This is called _function overloading_. 

## Function Overloading using Default Values

For example, we could create a function named `max()` that could take either two or three parameters:

```python
def main():
  max(2, 3)
  max(3, 4, 5)
  
def max(x, y, z=None):
  if z is not None:
    if x >= y:
      if x >= z:
        print(x)
      else:
        print(z)
    else:
      if y >= z:
        print(y)
      else:
        print(z)  
  else:
    if x >= y:
      print(x)
    else:
      print(y)
      
# main guard
if __name__ == "__main__":
  main()
```

In this example, we are calling `max()` with both 2 and 3 arguments from `main()`. When we only provide 2 arguments, the third parameter will be given the default value `None`, which is a special value in Python showing that the variable is empty. Then, we can use `if z is not None` as part of an **If-Then** statement to see if we need to take that variable into account in our code. 

This example also introduces a new keyword, `is`. The `is` keyword in Python is used to determine if two variables are exactly the same object, not just the same value. In this case, we want to check that `z` is exactly the same object as `None`, not just that it has the same value. In Python, it is common to use the `is` keyword when checking to see if an optional parameter is given the value `None`. We'll see this keyword again in a later chapter as we start dealing with objects. 

## Keyword Arguments

Python also allows us to specify function arguments using keywords that match the name of the parameter in the function. In that way, we can specify the arguments we need, and the function can use default values for any unspecified parameters. Here's a quick example:

```python
def main():
  args(1)             # 6
  args(1, 5)          # 9
  args(1, c=5)        # 8
  args(b=7, a=2)      # 12
  args(c=5, a=2, b=3) # 10
  
def args(a, b=2, c=3):
  print(str(a + b + c))
      
# main guard
if __name__ == "__main__":
  main()
```

In this example, the `args()` method has one required parameter, `a`. It can either be provided as the first argument, known as a _positional argument_, or as a _keyword argument_ like `a=2`. The other parameters, `b` and `c`, can either be provided as _positional arguments_ or _keyword arguments_, but they are not required since they have default values. 

Also, we can see that when we use keyword arguments we do not have to provide the arguments in the order they are defined in the function's definition. However, any arguments provided without keywords must be placed at the beginning of the function call, and will be matched positionally with the first parameters defined in the function. 

## Variable Length Parameters

Finally, Python allows us to define a single parameter that is a _variable length parameter_. In essence, it will allow us to accept anywhere from 0 to many arguments for that single parameter, which will then be stored in a list. Let's look at an example:

```python
def main():
  max(2, 3)
  max(3, 4, 5)
  max(5, 6, 7, 8)
  max(10, 11, 12, 13, 14, 15, 16)

def max(*values):
  if len(values) > 0:
    max = values[0]
    for value in values:
      if value > max:
        max = value
    print(max)

# main guard
if __name__ == "__main__":
  main()
```

Here, we have defined a function named `max()` that accepts a single variable length parameter. To show a parameter is variable length we use an asterisk `*` before variable name. We must respect two rules when creating a variable length parameter:

1. Each function may only have one variable length parameter
2. It must be defined after any positional parameters. Any parameters after the variable length parameter can only be assigned as keyword arguments 

So, when we run this program, we see that we can call the `max()` function with any number of arguments, and it will be able to determine the maximum of those values. Inside of the function itself, `values` can be treated just like a list.
